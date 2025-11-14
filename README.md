# AUTOMATIC-LED-CONTROL-USING-IR-SENSOR
##  AIM
To design and implement a system using the **STM32 microcontroller** where an LED automatically turns ON or OFF based on the input from an **IR sensor**.

---

##  Components Required
- STM32 Nucleo or Discovery Board (e.g., **Nucleo-G071RB**)
- IR Sensor Module
- LED (5mm Green or any color)
- Jumper wires
- Breadboard

---

##  Theory
An **IR sensor** detects the presence of an object by emitting and receiving infrared light.

### IR Sensor Behavior
- When an **object is detected**, the IR sensor output goes **LOW (0V)**.
- When **no object is detected**, the output stays **HIGH (3.3V)**.

### Microcontroller Response
- If **IR output = LOW** → **LED ON**
- If **IR output = HIGH** → **LED OFF**
### **Procedure**

1. Open **STM32CubeIDE**.
  ![WhatsApp Image 2025-10-29 at 07 38 26_4a6bb8af](https://github.com/user-attachments/assets/62ac4647-f7b9-42b6-9d63-5fa86a7e28d7)


2. Click **File → New STM32 Project**.
  ![WhatsApp Image 2025-10-29 at 07 53 44_edc0b9a6](https://github.com/user-attachments/assets/9169abdf-d301-4123-8cf2-1f2506c49393)
![WhatsApp Image 2025-10-29 at 07 53 26_b4c02626](https://github.com/user-attachments/assets/e4cda07f-35cf-40c9-9642-b9e481e5c705)


3. Select the **target microcontroller** or board and click **Next**.
  
![WhatsApp Image 2025-10-29 at 07 54 01_309b2e6d](https://github.com/user-attachments/assets/544b9ce6-6f37-4cf5-b4e1-527e8fb99004)



4. Name the project.
  
![WhatsApp Image 2025-11-14 at 10 41 26_82f44c10](https://github.com/user-attachments/assets/77119022-94b3-4fdb-8b68-8f8fd11cb0f0)

5. The corresponding `.ioc` file will be generated automatically.
  
![WhatsApp Image 2025-10-29 at 07 54 33_242d18db](https://github.com/user-attachments/assets/01e2e272-aae8-464f-9362-d9e42149eb53)

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
   ![WhatsApp Image 2025-10-29 at 07 54 52_6d91dd29](https://github.com/user-attachments/assets/d3cf1a10-3089-4f63-8b87-a4490b08d1ed)
![WhatsApp Image 2025-10-29 at 07 55 20_029adb5c](https://github.com/user-attachments/assets/34efabea-7615-4775-8b0c-7984addb1cba)

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
  
 ![WhatsApp Image 2025-10-29 at 07 55 50_d56c79ec](https://github.com/user-attachments/assets/e0213720-df3e-4973-8cfc-e564d882a17c)

8. Edit the generated main program as required.
![WhatsApp Image 2025-10-29 at 07 44 56_bafe7231](https://github.com/user-attachments/assets/e4571a14-1a5f-479e-ab77-5e2f4082f815)


9. Click **Project → Build All**.
    
![WhatsApp Image 2025-11-14 at 10 41 27_9e5f9b59](https://github.com/user-attachments/assets/b12d8dcf-6eb4-453b-84fd-f0c266b9cc23)

10. Link the **HEX file** using the post-build process.
  
![WhatsApp Image 2025-10-29 at 07 47 34_79d042c3](https://github.com/user-attachments/assets/792e4a41-ae3b-46ef-8e0e-1d8ef10b3899)

11. Click **Debug** and connect the **STM Nucleo Board**.
    <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/f72fff44-6073-4ae4-aa78-0da455df9af1" />

13. Click **Run** to execute the program.
    ![WhatsApp Image 2025-10-29 at 07 46 34_534b0f97](https://github.com/user-attachments/assets/aadf9473-ff27-436d-9eae-c7089850d9dd)

---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        GPIO_PinState ir = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_10); // IR OUT at PA10 (D2)

	      if (ir == GPIO_PIN_RESET)  // IR sensor HIGH = object detected
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET); // Turn ON LED
	      }
	      else
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_RESET); // Turn OFF LED
	      }

	      HAL_Delay(100);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 
![WhatsApp Image 2025-10-29 at 08 08 14_01e4164f](https://github.com/user-attachments/assets/25012429-b248-4ca3-a466-d667f1ddc9b8)

CASE 2: LED OFF
![WhatsApp Image 2025-10-29 at 08 08 15_586940b2](https://github.com/user-attachments/assets/e24a7b47-e49c-4fc2-9078-2c500e7b94f9)

---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




