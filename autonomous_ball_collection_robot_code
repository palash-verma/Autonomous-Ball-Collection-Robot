#include <Servo.h>

#define TRIGGER_PIN 3
#define ECHO_PIN    6
// Motor A connections
int bl1=8;
int bl2=7;
int bls=A2;
// Motor B connections
int br1=12;
int br2=13;
int brs=A0;

int fr1=10;
int fr2=11;
int frs=A3;
// Motor B connections
int fl1=5;
int fl2=4;
int fls=A1;

Servo armServo; // Servo motor for the arm

void setup() {
  pinMode(TRIGGER_PIN, OUTPUT);
  pinMode(ECHO_PIN, INPUT);
  pinMode(br1, OUTPUT);
  pinMode(br2, OUTPUT);

  pinMode(bl1, OUTPUT);
  pinMode(bl2, OUTPUT);

  pinMode(fl1, OUTPUT);
  pinMode(fl2, OUTPUT);

  pinMode(fr1, OUTPUT);
  pinMode(fr2, OUTPUT);

  pinMode(brs, OUTPUT);
  pinMode(bls, OUTPUT);
  pinMode(frs, OUTPUT);
  pinMode(fls, OUTPUT);
  
  armServo.attach(2); // Attach the servo to pin 3  
  Serial.begin(9600);
}

void loop() {
  armServo.write(0);
  long duration, distance;
  
  // Send pulse to trigger pin
  digitalWrite(TRIGGER_PIN, LOW);
  delayMicroseconds(2);
  digitalWrite(TRIGGER_PIN, HIGH);
  delayMicroseconds(10);
  digitalWrite(TRIGGER_PIN, LOW);
  
  // Read the pulse on echo pin
  duration = pulseIn(ECHO_PIN, HIGH);
  
  // Calculate distance in cm
  distance = duration * 0.034 / 2;
  
  // Print distance to serial monitor
  Serial.print("Distance: ");
  Serial.println(distance);
  delay(500);
  
  // If distance is less than a threshold, move towards the object
  if (distance < 40 && distance>10) { // Adjust the threshold as needed
    moveTowardsBall();
    Serial.println("moving");
    delay(50); // Adjust delay according to your robot's speed and response time
    stopMoving();
    delay(1000);
  }
  else if (distance<10){
    stopMoving();
    collectBall();
    Serial.println("collect ball");
    }
  else {
    // If the object is not within range, stop
    findBall();
    Serial.println("finding");
    delay(200);
  }
}

void stopMoving(){
  digitalWrite(br1, LOW);
  digitalWrite(br2, LOW);

  digitalWrite(bl1, LOW);
  digitalWrite(bl2, LOW);

  digitalWrite(fl1, LOW);
  digitalWrite(fl2, LOW);

  digitalWrite(fr1, LOW);
  digitalWrite(fr2, LOW);
  
}

void moveTowardsBall() {
  // Implement the movement logic here
  // For example, you can control the motors to move the robot towards the ball
  // Example:
  digitalWrite(br1, LOW);
  digitalWrite(br2, HIGH);
  
  digitalWrite(bl1, LOW);
  digitalWrite(bl2, HIGH);

  digitalWrite(fl1, HIGH);
  digitalWrite(fl2, LOW);

  digitalWrite(fr1, LOW);
  digitalWrite(fr2, HIGH); 

  analogWrite(brs,255);
  analogWrite(bls,255);
  analogWrite(frs,255);
  analogWrite(fls,255);

  delay(500);
}




void findBall() {
  // Stop the motors
  digitalWrite(br1, LOW);
  digitalWrite(br2, LOW);

  digitalWrite(bl1, LOW);
  digitalWrite(bl2, LOW);

  digitalWrite(fl1, LOW);
  digitalWrite(fl2, LOW);

  digitalWrite(fr1, LOW);
  digitalWrite(fr2, LOW);
  
  delay(200);

 digitalWrite(br1, LOW);
  digitalWrite(br2, HIGH);
  
  digitalWrite(bl1, HIGH);
  digitalWrite(bl2, LOW);

  digitalWrite(fl1, HIGH);
  digitalWrite(fl2, LOW);

  digitalWrite(fr1, LOW);
  digitalWrite(fr2, HIGH);

  analogWrite(brs,255);
  analogWrite(fls,255);
  analogWrite(bls,255);
  analogWrite(frs,255);

  delay(100);

  digitalWrite(br1, LOW);
  digitalWrite(br2, LOW);
  
  digitalWrite(bl1, LOW);
  digitalWrite(bl2, LOW);

  digitalWrite(fl1, LOW);
  digitalWrite(fl2, LOW);

  digitalWrite(fr1, LOW);
  digitalWrite(fr2, LOW);

   delay(1000);

}





void collectBall() {
 // Move the arm to collect the ball
  // for (int angle = 0; angle <= 180; angle++) {
  //   armServo.write(angle); // Increase angle gradually
  //   delay(10); // Adjust delay for desired speed
  // }
  // delay(1000); // Wait for the arm to reach the ball
  
  // for (int angle = 180; angle >= 0; angle--) {
  //   armServo.write(angle); // Decrease angle gradually
  //   delay(10); // Adjust delay for desired speed
  // }
  // delay(1000); // Wait for the arm to release the ball
  armServo.write(0);
  armServo.write(90);
  armServo.write(180);
  delay(500);
  armServo.write(180);
  armServo.write(90);
  armServo.write(0);

}
