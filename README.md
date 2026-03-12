## INTERFACING DAC WITH 8086 KIT AND GENERATING SQUARE AND SAWTOOTH WAVEFORMS

### AIM
To write an assembly language program in 8086 to generate square and Sawtooth waveforms using DAC.

### APPARATUS REQUIRED

| S. No | Item              | Specification   | Quantity |
|-------|------------------|-----------------|----------|
| 1     | Microprocessor kit | 8086            | 1        |
| 2     | Power Supply      | +5 V DC, +12 V DC | 1      |
| 3     | DAC Interface board | -              | 1        |



### ALGORITHM

### Measurement of Analog Voltage
1. Send the digital value to DAC.  
2. Read the corresponding analog value at its output.  

### Waveform Generation

#### Square Waveform
1. Send low value (00) to the DAC.  
2. Introduce suitable delay.  
3. Send high value to DAC.  
4. Introduce delay.  
5. Repeat the above procedure.  

#### Sawtooth Waveform
1. Load low value (00) to accumulator.  
2. Send this value to DAC.  
3. Increment the accumulator.  
4. Repeat step (ii) and (iii) until accumulator value reaches FF.  
5. Repeat the above procedure from step 1.  

---

### PROGRAMS

### 8086 Assembly Programs – DAC Interfacing

## Program: Square Wave
## Assembly Program  
| Memory Location | Program     | Comments                          |
|-----------------|-------------|-----------------------------------|
| 1000            | MOV AL,00H  | Load 00H in Accumulator           |
| 1003            |  OUT 0C8H,AL | Send through output port         |
| 1005            |  CALL DELAY(1100)  | CALL PROGRAM TO 1100      |
| 1008            |  MOV AL,0FFH |   Load 00H in Accumulator       |
| 100A            |   OUT 0C8H,AL|  Send through output port       |
| 100D            |  CALL DELAY(1100) | CALL PROGRAM TO 1100       |


| Memory Location | Program     | Comments                          |
|-----------------|-------------|-----------------------------------|
| 1100            | MOV CX,0505  | Load 0505H in Accumulator           |
| 1103            |  DEC CX | Decrement CX        |
| 1105           |  JNZ 1104  | RPEAT UNTILL ZERO      |
| 1108            |   RET |   RETURN TO MAIN PROGRAM      |


## Program: Sawtooth wave

## Assembly Program

| Memory Location | Program Instruction   | Comments                        |
|-----------------|-----------------------|---------------------------------|
| `1000`          | `START: MOV AL,00H`  | Load `00H` in accumulator       |
| `1003`          | `LOOP : OUT 0C8H,AL` | Send through output port        |
| `1005`          | `INC AL`             | Increment contents of accumulator |
| `1007`          | `JNC LOOP`           | Jump if no carry (continue loop) |
| `1009`          | `JMP START`          | Go to starting location         |



## Tabulation

| Waveform  | Amplitude | Time period | 
|-----------|-----------|-------------|
| Square    |  5V       |     2.5ms   | 
| Sawtooth  |   5V      |     2.5ms   |


### MODEL GRAPH
###### SAWTOOTH WAVEFORM   
<img width="503" height="358" alt="image" src="https://github.com/user-attachments/assets/afaa8723-44f4-40d1-b942-21c12acec946" />

###### SQUARE WAVEFORM   
<img width="499" height="360" alt="image" src="https://github.com/user-attachments/assets/e70c766b-8556-4109-9155-c2708b91ac61" />


### OUTPUT OF DAC USING DSO
###### SAWTOOTH WAVEFORM  
 <img width="531" height="299" alt="image" src="https://github.com/user-attachments/assets/56713a9e-c93f-4d91-876b-77f9014304bf" />

###### SQUARE WAVEFORM  
 <img width="533" height="357" alt="image" src="https://github.com/user-attachments/assets/a78e67ca-c3e1-4cba-91cf-efbde40456f2" />

### RESULT

Thus, the **DAC was interfaced with 8086** and different **waveforms** were successfully generated.




