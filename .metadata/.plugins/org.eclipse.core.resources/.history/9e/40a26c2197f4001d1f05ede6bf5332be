/***********************************************************************************************************************
 * Description: Measure the distance using ultrasonic sensor
 *              HC-SR04
 * Author: Sarah
 *********************************************************************************************************************/

#include"ultrasonic.h"
#include"lcd.h"
#include"icu.h"
#include<avr/io.h>
#include<util/delay.h>

uint16 Distance;
extern uint16 g_edgeCount;

int main(void)
{
	/*Enable global interrupt*/
	SREG |= (1<<7);
	/*Initialize Lcd*/
	LCD_init();

	while(1){

		/*Initialize Ultrasonic module*/
		Ultrasonic_init();

		Distance = Ultrasonic_readDistance();

		if (g_edgeCount == 2){
			ICU_deInit(); /* Disable ICU Driver */
			g_edgeCount = 0;

			LCD_displayStringRowColumn(0, 0, "distance=");

			LCD_moveCursor(0,10);

			if(Distance <100)
			{
				LCD_intgerToString(Distance);
				LCD_displayCharacter(' ');
			}
			else if(Distance<10)
			{

				LCD_intgerToString(Distance);
				LCD_displayCharacter(' ');
			}
			else
			{
				LCD_intgerToString(Distance);
			}
			LCD_displayStringRowColumn(0,14, "Cm");
		}
	}
}
