# Electronic-spartans
This project is done by another 7 people along with me. It's a minor project. In this mini project, the Automatic Room Lights using Arduino and Passive Infrared Sensor where the lights in the room will automatically turn ON and OFF by detecting the presence of a human. Such Automatic Room Lights can be implemented in your garages, staircases, bathrooms, etc where we don’t need continuous light but only when we are present. Also with the help of an automatic room light control system, there is no need to worry about electricity as the lights get automatically off when there is no person. So, in this project, we have implemented Automatic Room lights using Arduino and Passive Infrared Sensor. Arduino is a microcontroller which provides open source platform to perform software and hardware operations. This is an advantageous project as Arduino Uno and Passive Infrared Sensor is used thereby lights in the room will turn ON automatically by detecting a human motion and stay turned ON as long as the person remain present in the room. At the beginning, when no human is present the room, the Passive Infrared Sensor’s out pin is in the low mode. Hence, light of the room is OFF. The output of the Passive Infrared Sensor goes high as the person enters the room. Passive Infrared Sensor detects the infrared (IR) radiation in the room. The Digital pin 8 of Arduino is used to connect the data out pin of Passive Infrared Sensor. When this becomes high, the activation of relay takes place by Arduino. So that relay pin is in the low mode; because relay is an active low device. Now the lights will turn ON. This light maintains its state as ON as far there is motion in the room



Arduino CODE for the above project:
int in1 = 9;
int sensor = 8;
int led = 13;
unsigned long t=0;

void setup() 
{
  Serial.begin(9600);
  pinMode(in1, OUTPUT);
  pinMode(sensor, INPUT);
  pinMode(led, OUTPUT);
  
  digitalWrite(in1,HIGH);
  digitalWrite(led,LOW);

  while(millis()<13000)
  {
    digitalWrite(led,HIGH);
    delay(50);
    digitalWrite(led,LOW);
    delay(50);
  }
  digitalWrite(led,LOW);
  
}


void loop() 
{
  digitalWrite(in1,HIGH);
  digitalWrite(led,LOW);
  if(digitalRead(sensor)==HIGH)
  {
   t=millis();
   while(millis()<(t+5000))
   {
   digitalWrite(in1,LOW);
   digitalWrite(led,HIGH);
     if((millis()>(t+2300))&&(digitalRead(sensor)==HIGH))
      {
       t=millis();
      }
   }
  }
}
