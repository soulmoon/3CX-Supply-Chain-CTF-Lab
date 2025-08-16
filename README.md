# 3CX Supply Chain CTF Lab – CyberDefenders  

**Category**: Threat Intel  
**Tactics**:  
- Persistence  
- Privilege Escalation  
- Defense Evasion  
- Discovery  

**Tool Used**: VirusTotal  

---

A large multinational corporation heavily relies on the 3CX software for phone communication, making it a critical component of their business operations. After a recent update to the 3CX Desktop App, antivirus alerts flag sporadic instances of the software being wiped from some workstations while others remain unaffected. Dismissing this as a false positive, the IT team overlooks the alerts, only to notice degraded performance and strange network traffic to unknown servers. Employees report issues with the 3CX app, and the IT security team identifies unusual communication patterns linked to recent software updates.  

As the threat intelligence analyst, it's your responsibility to examine this possible supply chain attack. Your objectives are to uncover how the attackers compromised the 3CX app, identify the potential threat actor involved, and assess the overall extent of the incident.  

---

## 🔍 Questions and Answers  

**Q1**  
Understanding the scope of the attack and identifying which versions exhibit malicious behavior is crucial for making informed decisions if these compromised versions are present in the organization.  
**How many versions of 3CX running on Windows have been flagged as malware?**  
>> 2  
<img width="940" height="477" alt="image" src="https://github.com/user-attachments/assets/31212c81-84a1-475b-837f-d19ce07fc605" />

---

**Q2**  
Determining the age of the malware can help assess the extent of the compromise and track the evolution of malware families and variants.  
**What's the UTC creation time of the .msi malware?**  
>> 2023-03-13 06:33  
<img width="745" height="306" alt="image" src="https://github.com/user-attachments/assets/2a71ee96-3252-4a00-aa77-6b1cc1da2f62" />

---

**Q3**  
Executable files (.exe) are frequently used as primary or secondary malware payloads, while dynamic link libraries (.dll) often load malicious code or enhance malware functionality.  
**Which malicious DLLs were dropped by the .msi file?**  
>>  
- **ffmpeg.dll**  
  - SHA256 HASH: `7986bbaee8940da11ce089383521ab420c443ab7b15ed42aed91fd31ce833896`  
- **d3dcompiler_47.dll**  
  - SHA256 HASH: `11be1803e2e307b647a8a7e02d128335c448ff741bf06bf52b332e0bbf423b03`  
<img width="940" height="261" alt="image" src="https://github.com/user-attachments/assets/cf155de8-e278-4b1c-8979-ced87ff09b52" />

---

**Q4**  
Recognizing the persistence techniques used in this incident is essential for current mitigation strategies and future defense improvements.  
**What is the MITRE Technique ID employed by the .msi files to load the malicious DLL?**  
>> T1574  
<img width="940" height="442" alt="image" src="https://github.com/user-attachments/assets/3576fc0e-3944-44d4-bdcf-3df89975b662" />

---

**Q5**  
Recognizing the malware type (threat category) is essential to your investigation.  
**What is the threat category of the two malicious DLLs?**  
>> trojan  
<img width="940" height="344" alt="image" src="https://github.com/user-attachments/assets/709c770e-564d-4e7d-89d5-4c07a1bac2a5" />

---

**Q6**  
As a threat intelligence analyst conducting dynamic analysis, it's vital to understand how malware can evade detection in virtualized environments or analysis systems.  
**What is the MITRE ID for the virtualization/sandbox evasion techniques used by the two malicious DLLs?**  
>> T1497  
<img width="940" height="1092" alt="image" src="https://github.com/user-attachments/assets/2de0ca75-499f-4e78-a4fe-dcac869810f0" />

---

**Q7**  
When conducting malware analysis and reverse engineering, understanding anti-analysis techniques is vital.  
**Which hypervisor is targeted by the anti-analysis techniques in the ffmpeg.dll file?**  
>> VMware  
<img width="708" height="241" alt="image" src="https://github.com/user-attachments/assets/bf117695-f01a-44c6-a77a-bf26ebb5fad3" />

---

**Q8**  
Identifying the cryptographic method used in malware is crucial for understanding its techniques.  
**What encryption algorithm is used by the ffmpeg.dll file?**  
>> RC4  
<img width="940" height="432" alt="image" src="https://github.com/user-attachments/assets/c129de93-05ac-4975-949c-d6839ebdedf4" />

---

**Q9**  
As an analyst, you've recognized some TTPs involved in the incident, but identifying the APT group responsible will help you expand your investigation.  
**Which group is responsible for this attack?**  
>> Lazarus  
<img width="940" height="451" alt="image" src="https://github.com/user-attachments/assets/2a2901b5-b141-44a9-ae30-779cd175aada" />

---

## ✅ Lab Completed  
This lab provided insights into supply chain compromises, DLL hijacking, sandbox evasion, and attribution to state-sponsored APT groups.  

---
