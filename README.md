# Password-Checker

A Python-based password checker. Uses the [Have I Been Pwned API](https://haveibeenpwned.com/API/v3) to locally check whether an entered password(s) has been exposed in a data breach.

# How It Works

Using Python's built-in sys library, it takes in passwords entered after the file name on the command line interface e.g. `main.py hello thisisapassword`. 

The script itself sends a request to Have I Been Pwned's API endpoint to retrieve the possible tails of the hash of each entered password. Pwned Passwords, the specific API that this script uses, implements a k-Anonymity model "that allows a password to be searched for by a partial hash." This guarantees the safety of the entered password that the user wants to check, as the entire hash (and as a result the entire password) won't be transmitted across the internet. 

It checks the locally stored hash returned from Python's hashlib SHA1 function with each tail, returning how many times the password has appeared in their data set, otherwise it returns 0. If the password has been found even once, then it is deemed not secure to use and the output recommends a password change, otherwise no action is necessary.
