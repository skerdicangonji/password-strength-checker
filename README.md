# Password Strength Checker 🔒  

A simple Python script to evaluate password strength based on security best practices.  

## 🚀 Features  
✔️ Checks password length  
✔️ Detects uppercase, lowercase, numbers, and special characters  
✔️ Provides strength feedback (Weak, Moderate, Strong)  

## 🛠️ Usage  
1. Install Python (`python --version` to check)  
2. Run the script:  
   ```bash
   python password_checker.py

#---------------------------------------------------------------------------------------------------------#

import re  

def check_password_strength(password):
    strength = 0
    remarks = ""

    # Check length (at least 8 characters)
    if len(password) >= 8:
        strength += 1

    # Check for uppercase and lowercase
    if re.search(r'[A-Z]', password) and re.search(r'[a-z]', password):
        strength += 1

    # Check for digits
    if re.search(r'\d', password):
        strength += 1

    # Check for special characters
    if re.search(r'[!@#$%^&*()"<>.,]', password):  
        strength += 1

    # Evaluate strength and assign remarks based on the strength
    if strength == 4:
        remarks = "Strong Password "
    elif strength == 3:
        remarks = "Moderate Password "
    elif strength == 2:
        remarks = "Weak Password "
    else:
        remarks = "Very Weak Password! "

    return remarks

# Get user input
password = input("Enter a password to check its strength: ")
result = check_password_strength(password)

# Output the result
if result:
    print("Password Strength:", result)
else:
    print("Password does not meet the required criteria.")
