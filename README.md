# Lenovo K32-80 Hackintosh

OpenCore EFI for Lenovo Zhaoyang K32-80.

## Hardware
- **CPU**: Intel Core i5-7200U (Kaby Lake)
- **iGPU**: Intel HD Graphics 620
- **Storage**: SanDisk 256GB (M.2 SATA)
- **Wi-Fi**: Intel 8265 (Working)
- **OS**: macOS Ventura 13.7.8

## ⚠️ Known Issues & BIOS Requirements
- **Bluetooth Disabled**: Intel 8265 Bluetooth causes a `bluetoothd` crash loop during installation. I disabled the Bluetooth USB port in `UTBMap.kext` and blocked `IOBluetoothFamily` in `Kernel -> Block`. Buy a USB Bluetooth dongle if needed.
- **RAID Storage Fix**: This enterprise BIOS locks the SSD in RAID mode. Added `CtlnaAHCIPort.kext` to bypass this. You **MUST** disable `Security Chip` and `Intel SGX` in BIOS.
- **iGPU**: Using `00001659` as `AAPL,ig-platform-id`.

## Usage
1. **Generate your own SMBIOS!** Clear the Serial, MLB, UUID, and ROM in `PlatformInfo` and generate new ones. Do not use mine.
2. **Custom Kexts**: `UTBMap.kext` and `CPUFriendDataProvider.kext` are specific to this machine. Delete or regenerate them if you use this EFI on other models.

## Credits
Acidanthera & OpenIntelWireless.