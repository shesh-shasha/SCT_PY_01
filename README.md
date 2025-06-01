# Caesar Cipher Encryption & Decryption

#This Python program performs **Caesar Cipher encryption and decryption**.
def caesar_cipher_encrypt(text, shift):
    result = ""
    for char in text:
        if char.isalpha():
            base = ord('A') if char.isupper() else ord('a')
            result += chr((ord(char) - base + shift) % 26 + base)
        else:
            result += char
    return result

def caesar_cipher_decrypt(text, shift):
    return caesar_cipher_encrypt(text, -shift)

def main():
    while True:
        print("\n--- Caesar Cipher Menu ---")
        print("A. Encrypt")
        print("B. Decrypt")
        print("C. Exit")

        choice = input("Enter your choice (A/B/C): ").strip().upper()

        if choice == 'A':
            message = input("Enter the message to encrypt: ")
            try:
                shift = int(input("Enter the shift value: "))
            except ValueError:
                print("Shift value must be an integer.")
                continue
            encrypted = caesar_cipher_encrypt(message, shift)
            print("Encrypted message:", encrypted)

        elif choice == 'B':
            message = input("Enter the message to decrypt: ")
            try:
                shift = int(input("Enter the shift value: "))
            except ValueError:
                print("Shift value must be an integer.")
                continue
            decrypted = caesar_cipher_decrypt(message, shift)
            print("Decrypted message:", decrypted)

        elif choice == 'C':
            print("Exiting program. Goodbye!")
            break
        else:
            print("Invalid choice. Please choose A, B, or C.")

if __name__ == "__main__":
    main()

