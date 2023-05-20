# encrypt-Decrypt
from cryptography.fernet import Fernet

# Generate a random encryption key
def generate_key():
    key = Fernet.generate_key()
    with open('key.key', 'wb') as key_file:
        key_file.write(key)

# Load the encryption key
def load_key():
    try:
        with open('key.key', 'rb') as key_file:
            key = key_file.read()
            return key
    except FileNotFoundError:
        print("Encryption key not found. Please generate a key first.")

# Encrypt a file
def encrypt_file(file_path):
    key = load_key()
    if key:
        cipher_suite = Fernet(key)
        with open(file_path, 'rb') as file:
            file_data = file.read()
            encrypted_data = cipher_suite.encrypt(file_data)
        with open(file_path, 'wb') as encrypted_file:
            encrypted_file.write(encrypted_data)
        print(f"File {file_path} encrypted successfully.")
    else:
        print("Encryption key not found. Please generate a key first.")

# Decrypt a file
def decrypt_file(file_path):
    key = load_key()
    if key:
        cipher_suite = Fernet(key)
        with open(file_path, 'rb') as encrypted_file:
            encrypted_data = encrypted_file.read()
            decrypted_data = cipher_suite.decrypt(encrypted_data)
        with open(file_path, 'wb') as decrypted_file:
            decrypted_file.write(decrypted_data)
        print(f"File {file_path} decrypted successfully.")
    else:
        print("Encryption key not found. Please generate a key first.")
        
def encrypt_file(file_path):
    key = load_key()
    if key:
        cipher_suite = Fernet(key)
        with open(file_path, 'rb') as file:
            file_data = file.read()
            encrypted_data = cipher_suite.encrypt(file_data)
        with open(file_path, 'wb') as encrypted_file:
            encrypted_file.write(encrypted_data)
        print(f"File {file_path} encrypted successfully.")
    else:
        print("Encryption key not found. Please generate a key first.")


# Example usage
generate_key()
encrypt_file('secret.txt')
decrypt_file('secret.txt')
