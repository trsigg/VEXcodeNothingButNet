#pragma config(I2C_Usage, I2C1, i2cSensors)
#pragma config(Sensor, dgtl1,  Boom,           sensorRotation)
#pragma config(Sensor, dgtl2,  ArmDown,        sensorTouch)
#pragma config(Sensor, I2C_1,  ,               sensorQuadEncoderOnI2CPort,    , AutoAssign)
#pragma config(Sensor, I2C_2,  ,               sensorQuadEncoderOnI2CPort,    , AutoAssign)
#pragma config(Motor,  port2,           Launch1,       tmotorVex393_MC29, openLoop)
#pragma config(Motor,  port3,           Launch2,       tmotorVex393_MC29, openLoop, reversed)
#pragma config(Motor,  port4,           MiddleLeft,    tmotorVex393_MC29, openLoop, encoderPort, I2C_2)
#pragma config(Motor,  port5,           MiddleRight,   tmotorVex393_MC29, openLoop, reversed, encoderPort, I2C_1)
#pragma config(Motor,  port6,           BackLeft,      tmotorVex393_MC29, openLoop)
#pragma config(Motor,  port7,           BackRight,     tmotorVex393_MC29, openLoop, reversed)
#pragma config(Motor,  port8,           Feed,          tmotorVex393HighSpeed_MC29, openLoop)
#pragma config(Motor,  port9,           Ballmeter,     tmotorVex393HighSpeed_MC29, openLoop)


task main()
{
while (1==1)
	{
		motor[MiddleRight] = vexRT[Ch2];
		motor[MiddleLeft] = vexRT[Ch3];
		motor[BackRight] = vexRT[Ch2];
		motor[BackLeft] = vexRT[Ch3];
		if (SensorValue[ArmDown] == 1)
		{
			motor[Launch1] = 20;
			motor[Launch2] = 20;
		}
		else if (vexRT[Btn6U] == 1)
		{
			motor[Launch1] = 127;
			motor[Launch2] = 127;
		}
		else
		{
			motor[Launch1] = 20;
			motor[Launch2] = 20;
		}
			if (vexRT[Btn5U] == 1)
			{
				motor[Feed] = -127;
			}
			else if (vexRT[Btn5D] == 1)
			{
				motor[Feed] = 127;
			}
			else
			{
				motor[Feed] = 0;
			}
		if (vexRT[Btn7D] == 1)
		{
			motor[Ballmeter] = 20;
		}
		else
		{
			motor[Ballmeter] = 0;
		}
	}
}
