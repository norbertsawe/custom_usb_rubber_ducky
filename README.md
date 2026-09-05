# Nodus — RP2040 Custom USB Keystroke Injection Platform

**Nodus** is a custom, ultra-compact USB Human Interface Device (HID) platform designed for keystroke injection, automated penetration testing, and security research. Powered by the Raspberry Pi RP2040 microcontroller, the board features dedicated high-speed QSPI flash memory, a precision external crystal oscillator for reliable USB PHY timing, and hardware physical controls for rapid reset and bootloader recovery.

---

## 📷 Board Hardware Overview

<<<<<<< HEAD
The PCB is custom designed in a standard USB stick form factor with an integrated PCB USB-A plug:

```
<img width="526" height="403" alt="2026-09-05-162007_hyprshot" src="https://github.com/user-attachments/assets/fe85cdbf-8ad3-4a32-a78e-865f68fb89f0" />
=======
The PCB is custom designed in a standard USB stick form factor with an integrated PCB USB-A plug.
>>>>>>> 5fe3d07 (adding PCB images)


```

### Key Hardware Features

* **Microcontroller:** Raspberry Pi RP2040 Dual-Core ARM Cortex-M0+ running up to 133 MHz.
* **Storage:** High-speed QSPI NOR Flash IC for payload scripts and custom firmware storage.
* **Clock Source:** External 12 MHz Crystal Oscillator ensuring strict USB 2.0 full-speed timing stability.
* **On-Board Controls:**
* **`B` (BOOTSEL):** Physical tactile button to force UF2 bootloader mode upon startup.
* **`R` (RESET):** Hardware reset button for fast rebooting and rapid payload re-execution cycles without unplugging the drive.


* **Form Factor:** Slim, low-profile SMT design tailored for standard custom USB flash drive enclosures.

---

## 📊 Technical Specifications

| Component | Specification / Notes |
| --- | --- |
| **Core Processor** | RP2040 (Dual ARM Cortex-M0+, 264KB SRAM) |
| **Clock Source** | 12.000 MHz SMD Crystal Oscillator ($\pm$20 ppm) |
| **Flash Memory** | External QSPI NOR Flash (W25Qxx series or equivalent) |
| **Interface** | USB 2.0 Full-Speed (12 Mbps) Male USB-A Connector |
| **Power Supply** | 5V VBUS regulated via low-dropout (LDO) regulator to 3.3V |
| **Status Indicators** | Configurable User/Status LED(s) |
| **Debug & Control** | Tactical Boot/Reset switches, SWD target pads |

---

## 📁 Repository Structure

```
.
├── Docs/        # Technical datasheets, schematics exports, and PCB documentation
├── Firmware/    # C/C++ SDK project files, build configurations, and payload engines
├── Hardware/    # KiCad schematics (.kicad_sch), PCB layouts (.kicad_pcb), and Gerber outputs
└── README.md    # Project overview and instructions

```

---

## 🚀 Quickstart & Firmware Deployment

### 1. Putting the Board into Bootloader Mode

1. Plug the Nodus device into a host computer USB port.
2. Hold down the **`B` (BOOTSEL)** button and press the **`R` (RESET)** button once (or plug the device in while holding **`B`**).
3. Release the **`B`** button.
4. The device will enumerate as an external mass storage drive named `RPI-RP2`.

### 2. Flashing Binary Files

1. Compile your firmware using the Raspberry Pi Pico C/C++ SDK or CircuitPython / MicroPython.
2. Drag and drop your compiled `.uf2` file onto the mounted `RPI-RP2` drive.
3. The device will automatically reboot and start executing the payload instantly.

---

## 🛠 Building Firmware

If using the official C/C++ SDK:

```bash
cd Firmware
mkdir build && cd build
cmake ..
make -j$(nproc)

```

This generates the output `.uf2` binary ready for flashing.

---

> [!WARNING]
> **Security & Usage Disclaimer**
> This hardware platform is intended exclusively for authorized security auditing, educational purposes, penetration testing, and legitimate research activities. Always obtain explicit written permission from system owners before testing or running payloads on any host environment.

---

## 📜 License

This project is licensed under the MIT License. See the `LICENSE` file for details.
