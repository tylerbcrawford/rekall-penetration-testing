![Kali Linux](https://img.shields.io/badge/Kali_Linux-557C94?style=flat&logo=kalilinux&logoColor=white)
![Metasploit](https://img.shields.io/badge/Metasploit-2596CD?style=flat&logo=metasploit&logoColor=white)
![Burp Suite](https://img.shields.io/badge/Burp_Suite-FF6633?style=flat&logo=burpsuite&logoColor=white)
![Nmap](https://img.shields.io/badge/Nmap-4682B4?style=flat)

# Rekall Corporation — Penetration Testing Engagement

A 3-day authorized pen test against a fictional company's web application, Linux servers, and Windows servers. Team of three, UofT cybersecurity program (2024).

## What We Found

The environment was intentionally vulnerable, but the findings mirrored real-world patterns I've since seen referenced in CVE databases and OWASP reports:

- **SQL injection on the web app** — classic unsanitized input. We used Burp Suite to map the injection points and sqlmap to automate extraction. The app handed over its entire user table.
- **Remote code execution** — unpatched Apache Struts and Tomcat servers. Metasploit had modules ready to go for both. Once we had a shell, privilege escalation to root was straightforward through a misconfigured SUID binary.
- **Shellshock on Linux** — the bash vulnerability from 2014, still present. Nmap's scripting engine flagged it during the initial scan.
- **Weak credentials on Windows** — default and dictionary passwords on multiple accounts. John the Ripper cracked them in minutes. From there, lateral movement to domain admin was a short path through pass-the-hash.

Every finding led to either full system compromise or access to sensitive data. We documented exploitation steps, evidence, and remediation recommendations in the full report.

## Tools

Kali Linux, Metasploit Framework, Burp Suite, Nmap, Nikto, John the Ripper, Hashcat, Recon-ng

## Report

The full penetration test report with screenshots, exploitation chains, and remediation steps: **[Penetration Test Report (PDF)](Penetration_Test_Report.pdf)**

## Context

This was a capstone-style project for UofT's cybersecurity certificate program. Authorized testing in a sandboxed lab environment.
