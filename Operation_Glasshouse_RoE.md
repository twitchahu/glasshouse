
# Operation: Glasshouse

**Rules of Engagement (RoE)**

**Version:** 1.0  
**Issued by:** ahu  
**Date:** 20/06/2025

---

## 1. Mission Statement

Operation: Glasshouse is a full-scope adversary simulation designed to evaluate the effectiveness of Microsoft Sentinel and supporting systems when exposed to a custom red team framework (**KaylaRecon**) executed on a hardened Linux system (**RHEL 10 ARM64 on Raspberry Pi**). The objective is to measure detection capability, blue team responsiveness, and stealth persistence success under realistic attack conditions.

The system will be running Red Hat Enterprise Linux (RHEL) 10.0 ARM64 as a hardened Linux iteration is required for most analytic effect.

---

## 2. Objectives

### Red Team

- Deploy KaylaRecon modules in live environment
- Achieve persistence, lateral movement, and mock exfiltration
- Evade detection by Sentinel and alert-based systems
- Log all actions using `arcrunner.py` and `guardian.sh`
- Use of `EMP` and `Thatcher` modules is prohibited unless given permission by white team
- Use of `BOTRK` and `Monarch` is permitted

### Blue Team

- Monitor Azure Sentinel for indicators of compromise
- Detect and report anomalies in real time
- Use KQL to hunt for red team behavior
- Coordinate with white team for rule validation
- All monitoring tools are allowed unless:
  - Eternal framework
  - Invasive monitoring and lockdown tools
  - General lockdown tools

### White Team

- Document event timelines
- Ensure rules are followed by all sides
- Confirm integrity of logs and system state
- Deconflict gray areas and maintain fairness

---

## 3. Scope of Engagement

### Allowed:

- Execution of all KaylaRecon modules
- Log tampering simulation (must be reported by white team)
- Custom persistence (e.g., `monarch` user creation)
- Network disabling (`thatcher`, `emp`) with pre-warning to white team
- Use of root access on Pi target

### Forbidden:

- Use of malware, worms, or self-replicating binaries
- Real-world exfiltration or outbound payloads
- Attacks on infrastructure outside the Pi testbed
- Use of botnets, cloud DDoS, or external breach tools
- Kernel-level patching or bootloader modifications

---

## 4. Containment Measures

- All activity must remain on the Raspberry Pi and Azure-linked monitoring tools
- No public IP scanning or service exposure allowed
- Pi must be firewalled or airgapped except for Azure log agent
- Log rotation must be enforced to prevent resource exhaustion

---

## 5. Audit & Logging

- arcrunner.py and guardian.sh must be running during all red team operations
- Blue team must record all Sentinel detections with timestamps
- White team maintains a central opslog: `glasshouse_opslog.txt`

---

## 6. Operation Phases

### Phase 0: Recon/Setup

Red team prepares, white and blue teams ready monitoring infrastructure.

### Phase I: Breach

Stealth entry

### Phase II: Persistence

Establish presence

### Phase III: Disruption

Controlled use of disruption modules

### Phase IV: Post-Op Review

All teams submit logs, verdicts, and gap analyses

---

## 7. Victory Conditions

- **Red Team wins** if 3 or more major operations occur undetected
- **Blue Team wins** if 2 or more detections are made in real time and responded to

---
