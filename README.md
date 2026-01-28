# Understanding SQL Injection

A comprehensive guide to understanding SQL, SQL Injection vulnerabilities, exploitation techniques, and prevention strategies.

## 📚 Table of Contents

- [What is SQL?](#what-is-sql)
- [What is SQL Injection?](#what-is-sql-injection)
- [Repository Structure](#repository-structure)
- [Getting Started](#getting-started)

---

## What is SQL?

**SQL (Structured Query Language)** is a standardized programming language used to manage and manipulate relational databases. It allows users to create, read, update, and delete data stored in databases.

### Key SQL Concepts

**SQL is used for:**
- **Data Retrieval:** Fetching data from databases using SELECT queries
- **Data Insertion:** Adding new records using INSERT statements
- **Data Modification:** Updating existing records using UPDATE statements
- **Data Deletion:** Removing records using DELETE statements
- **Database Management:** Creating tables, indexes, and managing database structure

### Basic SQL Example

```sql
-- Retrieve all users from the users table
SELECT * FROM users WHERE username = 'john';

-- Insert a new user
INSERT INTO users (username, email, password) VALUES ('alice', 'alice@example.com', 'hashed_password');

-- Update user information
UPDATE users SET email = 'newemail@example.com' WHERE username = 'john';

-- Delete a user
DELETE FROM users WHERE username = 'john';
```

### SQL Database Systems

Common SQL database management systems include:
- **MySQL** - Open-source relational database
- **PostgreSQL** - Advanced open-source database
- **Microsoft SQL Server** - Enterprise database solution
- **Oracle Database** - Large-scale enterprise database
- **SQLite** - Lightweight embedded database

---

## What is SQL Injection?

**SQL Injection (SQLi)** is a critical security vulnerability that occurs when an attacker inserts malicious SQL code into input fields, allowing them to manipulate database queries and gain unauthorized access to sensitive data.

### How SQL Injection Works

SQL Injection happens when:
1. An application accepts user input
2. The input is directly concatenated into SQL queries without proper validation or sanitization
3. The malicious SQL code is executed by the database server
4. The attacker gains unauthorized access to data or can modify/delete records

### Vulnerable Code Example

```php
// VULNERABLE CODE - DO NOT USE IN PRODUCTION
$username = $_GET['username'];
$password = $_GET['password'];

// Direct concatenation - VULNERABLE!
$query = "SELECT * FROM users WHERE username = '" . $username . "' AND password = '" . $password . "'";
$result = mysqli_query($connection, $query);
```

### SQL Injection Attack Example

An attacker could input:
```
Username: admin' --
Password: anything
```

This transforms the query to:
```sql
SELECT * FROM users WHERE username = 'admin' --' AND password = 'anything'
```

The `--` comments out the password check, allowing login as admin without knowing the password.

### Types of SQL Injection

**1. Union-Based SQL Injection**
- Attacker uses UNION to combine results from multiple queries
- Extracts data from other tables

**2. Boolean-Based Blind SQL Injection**
- Attacker sends true/false conditions
- Infers data based on application responses

**3. Time-Based Blind SQL Injection**
- Attacker uses time delays to infer data
- Observes response times to determine true/false conditions

**4. Error-Based SQL Injection**
- Attacker triggers database errors
- Extracts information from error messages

**5. Stacked Queries SQL Injection**
- Attacker executes multiple SQL statements
- Can modify or delete data directly

### Impact of SQL Injection

SQL Injection can lead to:
- **Unauthorized Data Access:** Attackers can read sensitive information (usernames, passwords, personal data)
- **Data Modification:** Attackers can alter or corrupt database records
- **Data Deletion:** Critical data can be permanently deleted
- **Authentication Bypass:** Attackers can log in without valid credentials
- **Remote Code Execution:** In some cases, attackers can execute system commands
- **Complete System Compromise:** Full control over the database and potentially the entire application

### Real-World Impact

SQL Injection has been responsible for some of the largest data breaches:
- Millions of user records exposed
- Financial losses in billions of dollars
- Regulatory fines and legal consequences
- Damage to company reputation and customer trust

---

## Repository Structure

```
understand-sql-injection/
├── 01-sql-basics/           # SQL fundamentals and query structure
├── 02-injection-types/      # Different types of SQL injection attacks
├── 03-exploitation/         # Practical exploitation techniques
├── 04-prevention/           # Defense mechanisms and best practices
├── 05-labs/                 # Hands-on practice environments
├── 06-real-world-cases/     # Case studies and examples
└── README.md
```

---

## Getting Started

### Prerequisites
- Basic understanding of web applications
- Familiarity with databases
- Knowledge of HTTP requests
- Burp Suite or similar proxy tool (optional)

### How to Use This Repository

1. **Start with Basics:** Begin in `01-sql-basics/` to understand SQL fundamentals
2. **Learn Attack Types:** Study `02-injection-types/` to understand different SQL injection techniques
3. **Practice Exploitation:** Work through `03-exploitation/` with safe, legal environments
4. **Master Prevention:** Study `04-prevention/` to learn secure coding practices
5. **Hands-On Practice:** Use `05-labs/` for practical experience in controlled environments
6. **Analyze Cases:** Review `06-real-world-cases/` for real-world examples and lessons

### Important Notes

⚠️ **Ethical Guidelines:**
- All content in this repository is for educational purposes only
- Practice only in authorized environments (labs, CTFs, your own systems)
- Never attempt SQL injection on systems you don't own or have permission to test
- Responsible disclosure practices must be followed
- Unauthorized access to computer systems is illegal

---

## Learning Objectives

By completing this repository, you will:
- Understand how SQL databases work
- Recognize SQL injection vulnerabilities in code
- Learn multiple exploitation techniques
- Master prevention and mitigation strategies
- Develop secure coding practices
- Prepare for security certifications and interviews

---

## Resources

- [OWASP SQL Injection](https://owasp.org/www-community/attacks/SQL_Injection)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [PortSwigger SQL Injection](https://portswigger.net/web-security/sql-injection)
- [HackTheBox SQL Injection Challenges](https://www.hackthebox.com/)
- [PicoCTF SQL Injection Challenges](https://picoctf.org/)

---

## Contributing

This is a personal learning repository. Content will be added progressively as research and learning continue.

---

**Last Updated:** January 2026
**Author:** Tito Oscar Mwaisengela (@tito-devsec)
