# Enterprise Group Policy Management Lab

[![Windows Server 2022](https://img.shields.io/badge/Windows%20Server-2022-0078D6?logo=windows)](https://www.microsoft.com/windows-server)
![Active Directory](https://img.shields.io/badge/Active%20Directory-Lab-success)
![Group Policy](https://img.shields.io/badge/Group%20Policy-GPO-blue)
![VirtualBox](https://img.shields.io/badge/Oracle-VirtualBox-orange?logo=virtualbox)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

Enterprise Group Policy Management using Windows Server 2022 Active Directory.

## Table of Contents

- Overview
- Architecture
- Technologies Used
- Lab Objectives
- Environment
- Step-by-Step Deployment
- Group Policy Configuration
- Validation
- Troubleshooting
- Skills Demonstrated
- Future Improvements

## Environment

| Component | Configuration |
|-----------|---------------|
| Hypervisor | Oracle VirtualBox |
| Domain Controller | Windows Server 2022 |
| Client | Windows 11 Enterprise |
| DNS | Active Directory Integrated |
| Domain | company.local |
| Group Policy | Group Policy Management Console |

## Architecture

![Enterprise Architecture](images/architecture.png)

## Overview

This project demonstrates the deployment and administration of an enterprise Active Directory environment using Windows Server 2022. The lab focuses on centralized management through Organizational Units (OUs), Group Policy Objects (GPOs), DNS, and Windows 11 Enterprise clients.

## Technologies Used

- Windows Server 2022
- Active Directory Domain Services (AD DS)
- Group Policy Management
- DNS
- Windows 11 Enterprise
- Oracle VirtualBox

## Lab Objectives

- Deploy a Windows Server 2022 Domain Controller
- Configure Active Directory Domain Services
- Create Organizational Units (OUs)
- Create and manage Group Policy Objects (GPOs)
- Configure DNS for domain services
- Join Windows 11 clients to the domain
- Apply and validate Group Policy settings

## Skills Demonstrated

- Active Directory Administration
- Group Policy Management
- Windows Server Administration
- DNS Configuration
- Enterprise Network Design
- User and Computer Administration
- Security Policy Deployment
- Technical Documentation

# Screenshots

## Phase 1 – Environment Setup

### Enterprise OU Structure

Enterprise Organizational Unit (OU) hierarchy used to separate users, workstations, servers, and administrative functions.

![Enterprise OU Structure](images/Enterprise%20OU%20Structure.png)

### IT Users and Security Groups

IT Organizational Unit containing administrative users and security groups used for policy targeting.

![IT User](images/IT%20User.png)

### Domain-Joined Workstation

CLIENT01 successfully joined to the Active Directory domain and placed into the Workstations Organizational Unit.

![CLIENT01](images/CLIENT01%20in%20Workstations%20OU.png)

---

## Phase 2 – Group Policy Configuration

### Group Policy Management Console

Group Policy Management Console showing the configured GPOs and linked Organizational Units.

![Group Policy Management](images/Group%20Policy%20Management.png)

### IT User Restrictions GPO

Group Policy Object linked to the IT Organizational Unit.

![IT User Restrictions](images/IT%20User%20Restrictions%20Linked.png)

### Workstation Security Policy

Security policy linked to the Workstations Organizational Unit.

![Workstation Security Policy](images/Workstation%20Security%20Policy%20Linked.png)

---

## Phase 3 – Policy Configuration

### Disable Control Panel Policy

Administrative Template policy configured to prohibit Control Panel and PC Settings access.

![Control Panel Policy](images/Control%20Panel%20Policy.png)

### Disable Command Prompt Policy

Administrative Template policy configured to prevent Command Prompt access.

![Command Prompt Policy](images/Command%20Prompt%20Policy.png)

---

## Phase 4 – Policy Validation

### Control Panel Restriction Validation

Verification that Control Panel access is blocked by Group Policy.

![Control Panel Blocked](images/Control%20Panel%20Blocked.png)

### Command Prompt Restriction Validation

Verification that Command Prompt access is blocked through Group Policy.

![Command Prompt Blocked](images/Command%20Prompt%20Blocked.png)

## Step 1 - Install Windows Server 2022

- Create VirtualBox VM
- Configure networking
- Install Windows Server
- Apply updates

---

## Step 2 - Install Active Directory

- Install AD DS role
- Promote server to Domain Controller
- Configure DNS

---

## Step 3 - Create Organizational Units

- IT
- HR
- Finance
- Sales
- Workstations

---

## Step 4 - Create Users

- Test users
- Security groups
- Administrative accounts

---

## Step 5 - Join Windows 11 Client

- Configure DNS
- Join domain
- Verify authentication

---

## Step 6 - Configure Group Policies

Examples:

- Password Policy
- Account Lockout
- Desktop Wallpaper
- USB Restrictions
- Control Panel Restrictions
- Windows Updates

---

## Step 7 - Validate Policies

Commands used:

gpupdate /force

gpresult /r

gpresult /h report.html

## Repository Structure

```text
group-policy-management-lab/
├── docs/
├── images/
│   ├── architecture.drawio
│   ├── architecture.png
│   └── screenshots/
├── README.md
```

## Troubleshooting

### Issue: Client could not locate the domain

**Resolution:**
Verified that the Windows 11 client was using the Domain Controller as its primary DNS server and confirmed network connectivity before attempting to join the domain.

---

### Issue: Group Policy not applying

**Resolution:**
Verified the user/computer was located in the correct Organizational Unit (OU), confirmed the GPO was linked and enabled, and forced a policy refresh using `gpupdate /force`.

---

### Issue: Policy settings not taking effect

**Resolution:**
Used `gpresult` to verify which Group Policy Objects were applied and confirmed there were no security filtering or inheritance conflicts.

## Key Takeaways

- Designed an enterprise-style Active Directory Organizational Unit structure.
- Created and linked Group Policy Objects to specific Organizational Units.
- Implemented user and workstation security restrictions.
- Verified successful policy application using Group Policy Management and `gpresult`.
- Documented deployment steps and troubleshooting procedures.

## Future Enhancements

- Roaming Profiles
- Folder Redirection
- Fine-Grained Password Policies
- Windows Server Update Services (WSUS)
- Group Policy Preferences
- PowerShell Automation
