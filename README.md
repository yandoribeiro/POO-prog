# Código original

´´´
// C++ code
//
void setup()
{
  pinMode(12, OUTPUT);
  pinMode(3, INPUT_PULLUP);
  pinMode(4, INPUT_PULLUP);
  pinMode(5, INPUT_PULLUP);
  pinMode(6, INPUT_PULLUP);
  pinMode(7, INPUT_PULLUP);
  pinMode(8, INPUT_PULLUP);
  pinMode(9, INPUT_PULLUP);
  pinMode(10, INPUT_PULLUP);
}

void loop()
{
  while (digitalRead(3) == 0) { 
    tone(12, 262); 
  }
  while (digitalRead(4) == 0) { 
    tone(12, 294); 
  }
  while (digitalRead(5) == 0) { 
    tone(12, 330); 
  }
  while (digitalRead(6) == 0) { 
    tone(12, 349); 
  }
  while (digitalRead(7) == 0) { 
    tone(12, 392); 
  }
  while (digitalRead(8) == 0) { 
    tone(12, 440); 
  }
  while (digitalRead(9) == 0) { 
    tone(12, 493); 
  }
  while (digitalRead(10) == 0) { 
    tone(12, 523); 
  }
 
  noTone(12);
  
}

´´´

# Código em POO

´´´
class Tecla
{
private:
  int pin;
  int note;

public:
  Tecla(int p, int n): pin(p), note(n){
    pinMode(pin, INPUT_PULLUP);
  }

  bool isPressed() {
    return digitalRead(pin) == LOW;
  }

  int getNote() {
    return note;
  }
};

#define NUM_TECLAS 8

class Piano
{
private:
  Tecla* teclas[NUM_TECLAS];
  int numTeclas;

public:
  Piano(Tecla* t[], int n) {
    numTeclas = n;
    for (int i = 0; i < n; i++) {
      teclas[i] = t[i];
    }
  }
  
  void scanKeys() {
    for (int i = 0; i < numTeclas; i++) {
      if (teclas[i]->isPressed()) {
        playKey(i);
      }
    }
  }

    void playKey(int index) {
    int note = teclas[index]->getNote();
    tone(12, note);
    delay(200);
    noTone(12);
  }
};
´´´
