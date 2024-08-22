#include <LiquidCrystal.h>

#define BUTTON 13
#define BUTTON2 12
#define BUTTON3 11

#define RS 7
#define E 6
#define DB4 5
#define DB5 4
#define DB6 3
#define DB7 2

LiquidCrystal tela(RS, E, DB4, DB5, DB6, DB7);

int sec = 0;
int minut = 0;
int hour = 0;

void setup() {
  tela.begin(16, 2);
  pinMode(BUTTON, INPUT_PULLUP);
  pinMode(BUTTON2, INPUT_PULLUP);
  pinMode(BUTTON3, INPUT_PULLUP);
}

void loop() {
  int estadoBT = digitalRead(BUTTON);
  int estadoBT2 = digitalRead(BUTTON2);
  int estadoBT3 = digitalRead(BUTTON3);

  // Incrementar segundos
  if (sec < 60) {
    sec++;
  } else {
    sec = 0;
    minut++;
    if (minut >= 60) {
      minut = 0;
      hour++;
      if (hour >= 24) {
        hour = 0;
      }
    }
  }

  // Atualizar o display
  tela.setCursor(2, 1);
  if (hour < 10) tela.print("0");
  tela.print(hour);
  tela.print(":");
  if (minut < 10) tela.print("0");
  tela.print(minut);
  tela.print(":");
  if (sec < 10) tela.print("0");
  tela.print(sec);

  delay(10);  // Atraso de 1 segundo
}
	BUTTON=false 
      for BUTTON == tru
