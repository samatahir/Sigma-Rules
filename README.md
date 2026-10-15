# Sigma Detection Rules

![Sigma](https://img.shields.io/badge/Detection-Sigma-blue?style=flat-square)
![YAML](https://img.shields.io/badge/Format-YAML-red?style=flat-square)
![Cybersecurity](https://img.shields.io/badge/Focus-Detection%20Engineering-green?style=flat-square)

## About This Project

I created these Sigma rules to detect common attack techniques, including SSH brute-force attempts, suspicious Microsoft Office macro activity, and potential credential access through LSASS. This project focuses on writing detection logic in YAML and mapping rules to the MITRE ATT&CK framework.

## Detection Rules

### 1. SSH Brute-Force Detection

**File:** `rules/ssh_bruteforce.yml`

Detects failed SSH authentication attempts that may indicate password guessing or a brute-force attack.

- **Log source:** Linux SSH authentication logs
- **MITRE ATT&CK:** [T1110 — Brute Force](https://attack.mitre.org/techniques/T1110/)
- **What to investigate:** Source IP, targeted accounts, failed login frequency, and any subsequent successful logins.

### 2. Suspicious Office Macro Activity

**File:** `rules/office_macro_execution.yml`

Detects Microsoft Office applications launching command-line tools or script interpreters, which may indicate suspicious macro activity.

- **Log source:** Windows process creation events
- **MITRE ATT&CK:** [T1059 — Command and Scripting Interpreter](https://attack.mitre.org/techniques/T1059/)
- **What to investigate:** Parent process, command line, user account, and related process activity.

### 3. LSASS Process Access

**File:** `rules/lsass_access.yml`

Detects processes accessing LSASS, a Windows process that handles authentication. Unusual access may indicate an attempt to obtain credentials from memory.

- **Log source:** Windows Sysmon process access events
- **MITRE ATT&CK:** [T1003.001 — LSASS Memory](https://attack.mitre.org/techniques/T1003/001/)
- **What to investigate:** Source process, user, host, access details, and whether the activity is expected.

## Screenshots

The screenshots below help illustrate how each Sigma rule is structured and what the detection looks like in a SIEM.

### SSH Brute-Force Detection
![SSH Brute-Force Detection Rule](screenshots/ssh-bruteforce.png)

### Office Macro Detection
![Office Macro Detection Rule](screenshots/office-macro.png)

### LSASS Access Detection
![LSASS Access Detection Rule](screenshots/lsass-access.png)

## Tools & Skills

- Sigma
- YAML
- Detection Engineering
- MITRE ATT&CK
- Windows and Linux Security Logs
- Threat Detection
- False-Positive Analysis

## Testing and Validation

Sigma rules can be converted into queries for supported SIEM platforms using [Sigma CLI](https://github.com/SigmaHQ/sigma-cli).

Sigma CLI can be used to convert these rules into queries for supported SIEM tools.

Each rule should be tested with the right log data to make sure it works as expected. Reviewing the results also helps catch false positives and improve the rules.

## What I'm Learning

Through this project, I'm developing a better understanding of how detection rules are structured, how suspicious activity can be identified, and how security detections can support threat investigation and response workflows.

## Resources

- [Sigma Documentation](https://sigmahq.io/docs/)
- [SigmaHQ Rule Repository](https://github.com/SigmaHQ/sigma)
- [MITRE ATT&CK](https://attack.mitre.org/)

## Disclaimer

This is only an independent cybersecurity portfolio project. The rules are intended for educational purposes and should be Validated before being used in a production environment. 
