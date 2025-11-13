# calculator.py
#!/usr/bin/env python3
# calculator.py — Simple CLI Calculator

import sys

def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

def multiply(a, b):
    return a * b

def divide(a, b):
    if b == 0:
        return "Error: Division by zero"
    return a / b

def calculator():
    print("🧮 Welcome to the CLI Calculator!")
    print("Type 'exit' to quit.\n")

    while True:
        user_input = input("Enter operation (e.g., 3 + 5): ")

        if user_input.lower() in ["exit", "quit"]:
            print("Goodbye!")
            break

        try:
            parts = user_input.split()
            if len(parts) != 3:
                print("❌ Invalid format. Use: number operator number")
                continue

            a = float(parts[0])
            op = parts[1]
            b = float(parts[2])

            if op == '+':
                result = add(a, b)
            elif op == '-':
                result = subtract(a, b)
            elif op == '*':
                result = multiply(a, b)
            elif op == '/':
                result = divide(a, b)
            else:
                print(f"❌ Unknown operator: {op}")
                continue

            print(f"✅ Result: {result}\n")

        except ValueError:
            print("❌ Please enter valid numbers.\n")
        except Exception as e:
            print(f"⚠️ Error: {e}\n")

if __name__ == "__main__":
    calculator()
