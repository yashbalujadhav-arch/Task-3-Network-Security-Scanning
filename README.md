# Task-3-Network-Security-Scanning
Security analysis and lab walkthrough covering OWASP Top 10 vulnerabilities, Burp Suite testing, SQLi, and XSS for ApexPlanet Internship Task 3.
📌 Executive Summary
This repository contains the security analysis, laboratory walkthroughs, attack scenarios, and remediation strategies for Task 3: Web Application Security. The primary objective of this task is to identify, exploit, and mitigate critical web application vulnerabilities (referencing the OWASP Top 10) in a controlled laboratory environment.

🎯 Objectives
Set up and configure the DVWA (Damn Vulnerable Web Application) environment.

Intercept, analyze, and modify web traffic using Burp Suite.

Execute core web application attacks including SQL Injection (SQLi), Cross-Site Scripting (XSS), Cross-Site Request Forgery (CSRF), and File Inclusion.

Implement secure coding practices, prepared statements, and proper HTTP Security Headers.

🛠️ Lab Setup & Tools
Attacker Machine: Kali Linux

Target Machine/App: DVWA (Damn Vulnerable Web Application) / Metasploitable2

Core Security Tools:

Burp Suite: Web proxy, request manipulation, and Intruder fuzzing.

Browser DevTools / SecurityHeaders.com: Analysis of HTTP response headers and CSP policies.

🔍 Vulnerability Analysis & Attack Scenarios
1. SQL Injection (SQLi)
Exploitation: Executed input-based SQL injection to bypass authentication and extract user credentials from the backend database.

Impact: Unauthorized data exposure, potential administrative access, and data manipulation.

Mitigation: Implemented Parameterized Queries (Prepared Statements) using PDO/MySQLi to separate executable code from user data.

2. Cross-Site Scripting (XSS)
Reflected XSS: Injected malicious scripts via HTTP query parameters to execute client-side code in the victim's browser session.

Stored XSS: Injected persistent JavaScript payloads into input fields stored directly in the application database.

Mitigation: Enforced strict Input Sanitization/Contextual Encoding and configured a robust Content Security Policy (CSP) header.

3. Cross-Site Request Forgery (CSRF)
Exploitation: Crafted an unauthorized request state to alter sensitive account details (such as password changes) without the victim's explicit consent.

Mitigation: Integrated unique, unpredictable Anti-CSRF Tokens validated on every state-changing server request.

4. File Inclusion (LFI / RFI)
Local File Inclusion (LFI): Manipulated path parameters to read internal system files (/etc/passwd).

Remote File Inclusion (RFI): Loaded external scripts to achieve remote code execution.

Mitigation: Restricted directory pathing and disabled allow_url_include directives in PHP configurations.

5. Burp Suite Advanced Testing & Web Security Headers
Request Fuzzing: Utilized Burp Suite Intruder to brute-force parameters and test endpoint resilience.

Security Headers Implementation: Evaluated response headers and updated server configurations (e.g., Apache/Nginx) to enforce:

Strict-Transport-Security (HSTS)

X-Content-Type-Options: nosniff

X-Frame-Options: DENY

Content-Security-Policy

📑 Key Takeaways & Remediation Summary
Security must be integrated into the development lifecycle through secure coding practices rather than relying solely on perimeter defenses.

Always validate and sanitize user inputs on the server side.

Proper HTTP header configurations add critical defense-in-depth protection against common client-side exploits.
