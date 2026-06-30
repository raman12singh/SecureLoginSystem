# Secure Login System (Java)

A console-based authentication system built in Java that demonstrates secure password handling and brute-force attack prevention — built for learning core application security concepts.

## Features

- **User Registration** with enforced password strength rules
- **Secure Password Storage** using SHA-256 hashing combined with a unique per-user salt
- **Brute Force Protection** — accounts lock automatically after repeated failed login attempts
- **Auto-Unlock** — lockout expires automatically after a cooldown period
- **Generic Error Messages** — login failures don't reveal whether a username exists, preventing username enumeration
- **Colorful CLI Interface** using ANSI escape codes for a clean terminal experience

## Security Highlights

| Feature | Implementation |
|---|---|
| Password Hashing | SHA-256 with salt (`SecureRandom`-generated, 16 bytes, Base64-encoded) |
| Brute Force Defense | Max 3 failed attempts → 30 second lockout |
| Password Policy | Min 8 characters, requires uppercase, lowercase, digit, and special character |
| Information Leakage Prevention | Same error message for "user not found" and "wrong password" |

## How It Works

1. **Register** — Create a username and password. The password is validated against strength rules, then hashed with a randomly generated salt before being stored in memory.
2. **Login** — Enter your credentials. The entered password is hashed using the stored salt and compared against the stored hash.
3. **Lockout** — After 3 incorrect attempts, the account is locked for 30 seconds. Attempts reset automatically once the lockout window expires.

## Getting Started

### Prerequisites
- Java JDK 17 or later

### Run the Program

```bash
javac SecureLoginSystem.java
java SecureLoginSystem
```

### Usage

```
1️⃣  Register   — create a new account
2️⃣  Login      — authenticate with existing credentials
3️⃣  Exit       — quit the application
```

## Project Structure

```
SecureLoginSystem.java   # Single-file implementation: UI, registration, login, hashing, lockout logic
```

## Notes

- User data is stored **in memory only** (a `HashMap`); it resets when the program exits. This project is intended as a security concepts demo, not a production-ready authentication system.
- For production use, consider a persistent database, a slow hashing algorithm designed for passwords (e.g., bcrypt, Argon2, or PBKDF2) instead of plain SHA-256, and HTTPS/TLS if exposed over a network.

## License

MIT License — feel free to use and modify for learning purposes.

---

Want me to also add a `.gitignore`, a `LICENSE` file, or badges (build status, Java version) to round out the repo?
