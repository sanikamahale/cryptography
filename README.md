# cryptography
encrytor.py 

from cryptography.fernet import Fernet

# Function to generate a key and save it
def generate_key():
    key = Fernet.generate_key()
    with open("key.key", "wb") as key_file:
        key_file.write(key)

# Function to load the key
def load_key():
    return open("key.key", "rb").read()

# Function to encrypt a file
def encrypt_file(filename, key):
    f = Fernet(key)
    with open(filename, "rb") as file:
        data = file.read()
    encrypted = f.encrypt(data)
    with open(filename, "wb") as file:
        file.write(encrypted)

# Function to decrypt a file
def decrypt_file(filename, key):
    f = Fernet(key)
    with open(filename, "rb") as file:
        data = file.read()
    decrypted = f.decrypt(data)
    with open(filename, "wb") as file:
        file.write(decrypted)

        main.py 

        from encryptor import generate_key, load_key, encrypt_file, decrypt_file

print("---- Advanced AES Encryption Tool ----")

choice = input("Do you want to (G)enerate Key, (E)ncrypt, or (D)ecrypt? ").upper()

if choice == "G":
    generate_key()
    print("✅ Key generated and saved as key.key")
elif choice == "E":
    key = load_key()
    file = input("Enter filename to encrypt (e.g. secret.txt): ")
    encrypt_file(file, key)
    print("🔐 File encrypted successfully!")
elif choice == "D":
    key = load_key()
    file = input("Enter filename to decrypt: ")
    decrypt_file(file, key)
    print("🔓 File decrypted successfully!")
else:
    print("❌ Invalid choice. Please choose G,E or D.")
