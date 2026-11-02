# Sequential Heart-Shaped LED Chaser Circuit

A symmetrical, 18-LED heart-shaped chaser circuit driven by an **NE555 timer** and two **CD4017 decade counters**. The circuit generates a continuous, smooth light sequence flowing simultaneously from top to bottom on both sides of the heart shape.

---

## 🛠️ Components List

| Component | Quantity | Description / Note |
| :--- | :--- | :--- |
| **NE555 Timer IC** | 1 | Clock generator (Astable Oscillator) |
| **CD4017 CMOS Decade Counter** | 2 | Sequential pulse decoders (Left & Right channels) |
| **5mm Red LEDs** | 18 | High-brightness 5mm red LEDs |
| **220 Ohm Resistors** | 18 | Current-limiting resistors for LEDs |
| **1k Ohm Resistors (RA, RB)** | 2 | NE555 RC timing network resistors |
| **100µF Electrolytic Capacitor (C1)** | 1 | NE555 RC timing network capacitor (16V+ rated) |
| **Protoboard / Perforated PCB** | 1 | Circuit assembly board |
| **Power Source** | 1 | 5V DC (USB) or 9V Battery |

---

## 📐 Circuit Connections & Pinout

### 1. NE555 Clock Generator

| NE555 Pin | Connection Target |
| :--- | :--- |
| **Pin 1 (GND)** | Common Ground / GND (-) |
| **Pin 2 (TRIG)** | Shorted to **Pin 6** + **100µF (C1)** (+) terminal |
| **Pin 3 (OUT)** | **CD4017 IC1 Pin 14** & **CD4017 IC2 Pin 14** (Common Clock Line) |
| **Pin 4 (RESET)**| **+VCC** (+5V / +9V) |
| **Pin 5 (CTRL)** | Unconnected / Floating |
| **Pin 6 (THRES)**| Shorted to **Pin 2** |
| **Pin 7 (DISCH)**| Tied to **+VCC** via **RA (1k Ohm)** <br> Tied to **Pin 2/6 Bridge** via **RB (1k Ohm)** |
| **Pin 8 (VCC)**  | **+VCC** (+5V / +9V) |

* **C1 (100µF):** Anode (+) to **Pin 2/6 Bridge**, Cathode (-) to **Common GND**.

---

### 2. CD4017 Decade Counters (Dual Channel)

Both CD4017 ICs receive the exact same clock pulse from NE555 Pin 3 to ensure perfect symmetrical execution.

#### IC1 - Left Wing & IC2 - Right Wing

| CD4017 Pin | Connection Target |
| :--- | :--- |
| **Pin 16 (VDD)** | **+VCC** (+5V / +9V) |
| **Pin 8 (VSS)**  | **Common GND** (-) |
| **Pin 13 (CP1 / Enable)** | **Common GND** (-) *(Enables output counting)* |
| **Pin 15 (RESET)** | **Common GND** (-) *(Ensures full 10-step sequence)* |
| **Pin 14 (CP0 / Clock)** | **NE555 Pin 3 (Output)** |

---

### 3. LED Outputs Mapping

The logical outputs (Q0–Q8) of each CD4017 IC are connected through 220 Ohm resistors to the corresponding LEDs on each side of the heart:

| Step | CD4017 Output Pin | Left LED (IC1) | Right LED (IC2) |
| :---: | :---: | :---: | :---: |
| **1** | **Pin 3 (Q0)**  | LED L1 (Top Center) | LED R1 (Top Center) |
| **2** | **Pin 2 (Q1)**  | LED L2 | LED R2 |
| **3** | **Pin 4 (Q2)**  | LED L3 | LED R3 |
| **4** | **Pin 7 (Q3)**  | LED L4 | LED R4 |
| **5** | **Pin 1 (Q4)**  | LED L5 | LED R5 |
| **6** | **Pin 5 (Q5)**  | LED L6 | LED R6 |
| **7** | **Pin 6 (Q6)**  | LED L7 | LED R7 |
| **8** | **Pin 9 (Q7)**  | LED L8 | LED R8 |
| **9** | **Pin 11 (Q8)** | LED L9 (Bottom Tip) | LED R9 (Bottom Tip) |

* **LED Anodes (+):** Connected to individual 220 Ohm resistors from CD4017 outputs.
* **LED Cathodes (-):** Soldered together forming a single continuous **Common GND Ring** along the rear of the board.

---

## ⚡ Working Principle

1. **Astable Oscillation:** The NE555 timer operates in astable mode, continuously charging and discharging C1 through RA and RB to produce a square wave clock signal on Pin 3.
2. **Symmetrical Decoding:** The clock output from NE555 Pin 3 drives Pin 14 of both CD4017 counters simultaneously.
3. **Sequential Output:** On each rising clock edge, both CD4017 ICs advance their active high output from Q0 through Q8, creating a fluid, dual-sided flowing light sequence.

---

## 🔋 Power Options

- **9V PP3 Battery:** Provides portable, bright, and highly stable operation.
<img width="561" height="607" alt="image" src="https://github.com/user-attachments/assets/5f368c5c-3c28-4596-a9d1-49cab993ffcc" />
<img width="561" height="711" alt="image" src="https://github.com/user-attachments/assets/a7b3a2e5-b89b-46dd-8815-08141aa90d6b" />







https://github.com/user-attachments/assets/39ea5f55-a13d-4a83-9a2f-853705d693f0



