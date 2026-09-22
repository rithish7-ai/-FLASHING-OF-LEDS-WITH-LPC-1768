# FLASHING-OF-LEDS-WITH-LPC-1768 and Arduino

# AIM: 
   To interface and toggle the led with ARM LPC 1768 microprocessor and Arduino        
           
# COMPONENTS REQUIRED:
##  HARDWARE:
ARM LPC1768

LED

ARDUINO BOARD
## SOFTWARE:
KEIL MICRO VISION 4.0 IDE

ARDUINO IDE

# PROCEDURE:
⮚	Open the Keil software and select the New uvision project from Project Menu as shown below.
⮚	Browse to your project folder and provide the project name and click on save.

⮚	Once the project is saved a new pop up “Select Device for Target” opens, Select the controller (NXP: LPC1768) from NXP (founded by philips) and click on OK.
⮚	Select the controller (NXP: LPC1768) and click on OK.

⮚	As LPC1768 needs the startup code, click on Yes option to include the LPC17xx Startup file.
⮚	Create a new file by file → new to write the program.

⮚	Type the code.

⮚	After typing the code save the file as main.c eg. (abc.c).

⮚	Right click target and Add the suitable files to source group1 and header.
 
⮚	Add the main.c along with system_LPC17xx.c.

⮚	Build the project and fix the compiler errors/warnings if any.

⮚	Code is compiled with no errors. The .bin file is still not generated.
⮚	Right Click on Target Options to select the option for generating .bin file.

⮚	Set IROM1 start address as 0x2000. Bootloader will be stored from 0x0000-0x2000 so application should start from 0x2000

⮚	Write	the	command	to	generate	the .bin file	from
.axf file 
Command: fromelf --bin projectname.axf --output filename.bin
⮚	in c/c++ → include paths → desktop (00-libfiles).

⮚	.Bin file is generated after a rebuild.

⮚	Check the project folder for the generated .Bin file.

# ADD FILES:

Target1:
Source group1:
Startuplpc17xx.s, delay.c , gpio.c , sysytemlpc17xx.c, main.c
Header:
delay.h, gpio.h, stdulils.h
 
# PIN DIAGRAM :

<img width="767" height="416" alt="image" src="https://github.com/user-attachments/assets/1afc7473-7913-488b-a649-7b4a6a9db4cc" />

# CIRCUIT DIAGRAM:

<img width="715" height="366" alt="image" src="https://github.com/user-attachments/assets/512e671c-7d7e-4e65-8cef-cd005e526bcf" />

# PROGRAM:
```C
#include <lpc17xx.h>
#include "delay.h"       //User defined library which contains the delay routines
#include "gpio.h"

#define LED P1_29        // Led is connected to P1.29

/* start the main program */
int main()
{
    SystemInit();                          //Clock and PLL configuration
    GPIO_PinFunction(LED,PINSEL_FUNC_0);   // Configure Pin for Gpio
    GPIO_PinDirection(LED,OUTPUT);         // Configure the pin as OUTPUT
    GPIO_PinWrite(LED,LOW);

    while(1)
    {
        /* Turn On all the leds and wait for 100ms */
        GPIO_PinWrite(LED,HIGH);           // Make all the Port pin as high
        DELAY_ms(100);

        GPIO_PinWrite(LED,LOW);            // Make all the Port pin as low
        DELAY_ms(100);
    }
}
```
## ARDUINO PROGRAM:
```
void setup() {
  pinMode(LED_BUILTIN, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  digitalWrite(LED_BUILTIN, HIGH);
  Serial.println("LED ON");
  delay(1000);

  digitalWrite(LED_BUILTIN, LOW);
  Serial.println("LED OFF");
  delay(1000);
}

```
 
# Output:

<img width="647" height="472" alt="image" src="https://github.com/user-attachments/assets/4fb09954-d4b6-47bd-9f05-33de7ce20c5d" />

## ARDUINO OUTPUT:
<img width="873" height="131" alt="image" src="https://github.com/user-attachments/assets/3abf0731-6cb3-4cac-82ae-86ff69de4277" />

# Result :
Thus, a LED is interfaced and toggled with ARM LPC1768 Microprocessor and Arduino



