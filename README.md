# Password-Generator

import tkinter as tk
import random
import string

def generate_password():
    length = int(length_entry.get())
    characters = ""
    if var_upper.get():
        characters += string.ascii_uppercase
    if var_lower.get():
        characters += string.ascii_lowercase
    if var_digits.get():
        characters += string.digits
    if var_special.get():
        characters += string.punctuation

    if not characters:
        password_label.config(text="Select at least one option")
        return

    password = ''.join(random.choice(characters) for _ in range(length))
    password_label.config(text=password)

root = tk.Tk()
root.title("Password Generator")
root.geometry("400x300")

tk.Label(root, text="Password Length:").pack(pady=5)
length_entry = tk.Entry(root, width=10)
length_entry.pack(pady=5)
length_entry.insert(0, "12")

var_upper = tk.BooleanVar(value=True)
var_lower = tk.BooleanVar(value=True)
var_digits = tk.BooleanVar(value=True)
var_special = tk.BooleanVar(value=False)

tk.Checkbutton(root, text="Include Uppercase", variable=var_upper).pack()
tk.Checkbutton(root, text="Include Lowercase", variable=var_lower).pack()
tk.Checkbutton(root, text="Include Numbers", variable=var_digits).pack()
tk.Checkbutton(root, text="Include Special Characters", variable=var_special).pack()

tk.Button(root, text="Generate Password", command=generate_password).pack(pady=10)

password_label = tk.Label(root, text="", font=('Arial', 14), fg='blue')
password_label.pack(pady=10)

root.mainloop()
