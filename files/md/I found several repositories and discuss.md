I found several repositories and discussions related to Discord webhook stealers and information-stealing malware that impersonate legitimate software. Let me provide you with comprehensive information about this threat:

## Overview: Discord Webhook Stealer Malware

The virus you're describing is an **information stealer (infostealer)** that uses Discord webhooks for data exfiltration. This is a widespread class of malware active in 2025-2026.

---

## How the Virus Works

### **1. Distribution Method**

- **Fake websites** impersonating legitimate software (microphone apps, game cheats, productivity tools)
- **Typosquatting** domains that look like official sites
- **Social engineering** on Discord, Telegram, gaming forums
- **Malvertising** and YouTube video descriptions

### **2. Infection Chain**

```
Victim downloads file → Runs .exe/.py → Malware executes → Data stolen → Sent to Discord webhook → Hacker notified
```

### **3. Data Exfiltration via Discord Webhook**

Discord webhooks are abused because they:

- Are **free** and require no authentication
- Accept **large file uploads** (up to 25MB)
- Provide **instant notifications** to the attacker's Discord server
- Are **hard to trace** back to the attacker
- Often **bypass firewalls** (Discord is rarely blocked)

---

## What the Virus Steals

Based on the GitHub repositories found, typical Discord webhook stealers collect:

### **Credentials & Tokens**

- Discord tokens (from 30+ browsers + Discord app)
- Browser passwords (Chrome, Edge, Firefox, Opera, etc.)
- Browser cookies (session hijacking)
- Credit card information (autofill data)
- Roblox `.ROBLOSECURITY` cookies
- Cryptocurrency wallet files

### **System Information**

- Public/local IP addresses
- Geolocation (country, city, ISP)
- Hardware ID (HWID)
- CPU, GPU, RAM details
- Operating system version
- Screenshots

### **Files**

- SSH keys (`~/.ssh/`)
- AWS credentials (`~/.aws/`)
- Kubernetes configs (`~/.kube/`)
- Git credentials
- Browser history & downloads

---

## Recent Real-World Example: RedTiger Stealer

From the search results, I found a **detailed analysis** of the **RedTiger Stealer** family (see issue [#1 in Blackeige/ZeroTrace-Tools](https://github.com/Blackeige/ZeroTrace-Tools/issues/1)):

### **Technical Details**

- **C2 Domain**: `redtiger.shop`
- **Exfil Method**: Discord webhook (AES-256-CBC encrypted URL)
- **Target**: Windows only
- **Obfuscation**: Random long variable names, encrypted config
- **Persistence**: Copies itself to Windows Startup folder with invisible Unicode filename

### **Capabilities**

- Injects malicious JavaScript into Discord desktop client for **persistent backdoor**
- Intercepts Discord logins, password changes, payment methods
- Auto-purchases Discord Nitro using victim's cards
- Steals from 21+ browsers across multiple profiles

---

## How to Protect Yourself

### **Prevention**

1. ✅ **Only download from official sources** (verified publishers)
2. ✅ **Check URLs carefully** for typos (e.g., `microfone.com` vs `microphone.com`)
3. ✅ **Use antivirus software** with real-time protection
4. ✅ **Enable Windows SmartScreen** and UAC prompts
5. ✅ **Verify file signatures** before running executables

### **Detection**

Check for these indicators:

- New files in `%APPDATA%\Microsoft\Windows\Start Menu\Programs\Startup\`
- Unusual Discord `index.js` file (should be <5KB, malicious ones are >20KB)
- Unknown processes calling Discord webhooks (check firewall logs)
- Sudden Discord token invalidation (gets stolen and used elsewhere)

### **If Infected - Immediate Actions**

1. 🔴 **Disconnect from internet** immediately
2. 🔴 **Change ALL passwords** from a clean device
3. 🔴 **Revoke Discord tokens** (logout all sessions)
4. 🔴 **Remove stored payment methods** from browsers
5. 🔴 **Run malware removal tools**:
   - Windows Defender Offline Scan
   - Malwarebytes Anti-Malware
   - HitmanPro
6. 🔴 **Reinstall Discord** (to remove injected code)
7. 🔴 **Check bank/crypto accounts** for unauthorized access
8. 🔴 **Rotate SSH keys and API tokens**

---

## Educational Resources

### **Legitimate Projects for Research**

- [Discord Token Protector](https://github.com/Elliesaur/DiscordProtect) - Prevents token theft on Windows
- [DisGuard](https://github.com/PwnTheStack/DisGuard) - Real-time Discord stealer detection tool

### **Malware Analysis Reports**

Several security researchers have documented these threats:

- **RedTiger Stealer** analysis (see GitHub issue linked above)
- **LiteLLM supply chain attack** (2026-03-24) - Malicious Python package stealing credentials via `.pth` files
- **Python File Stealer** repositories (educational only, **DO NOT execute**)

---

## Why This Keeps Happening

1. **Low barrier to entry**: Stealer builders are sold on darknet markets
2. **High profitability**: Stolen accounts/crypto are monetized quickly
3. **Weak user awareness**: Many users trust "friend recommendations" on Discord
4. **Platform abuse**: Discord doesn't rate-limit webhook abuse effectively
5. **Obfuscation tools**: AutoPy2Exe, PyArmor make detection harder

---

## Reporting Malicious Sites

If you encounter a fake site:

- **Discord**: Report to https://dis.gd/request (Terms of Service violation)
- **Google Safe Browsing**: https://safebrowsing.google.com/safebrowsing/report_phish/
- **Microsoft SmartScreen**: https://www.microsoft.com/en-us/wdsi/support/report-unsafe-site
- **Domain registrar**: WHOIS lookup → abuse contact

---

## Sources from GitHub Search

1. [RedTiger Stealer Analysis](https://github.com/Blackeige/ZeroTrace-Tools/issues/1) - Full technical breakdown
2. [LiteLLM Compromise](https://github.com/BerriAI/litellm/issues/24512) - Supply chain attack via PyPI (March 2026)
3. [Discord Infostealer Monitoring](https://github.com/StuxMirai/Discord-Infostealer-Monitoring) - Phishing campaign tracker
4. [Multiple stealer repositories](https://github.com/search?q=discord+webhook+stealer) - Educational/research purposes

---

**⚠️ Final Warning**: Never run code from untrusted sources, even "to test it". These malware families are highly sophisticated and can steal credentials in milliseconds. Always verify software authenticity through official channels.

If you have specific questions about a suspicious file or website, share details (WITHOUT executing anything) and I can help analyze it safely.
