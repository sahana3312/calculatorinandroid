## EX:NO:05:Develop a program to create a simple calculator using android studio.
## Aim:
To create and design an android application for a simple calculator using android studio.
## EQUIPMENTS REQUIRED:
Android Studio(Latest Version)
## ALGORITHM:
Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as smsintent and click Next.

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6:Display details give in MainActivity file.

Step 7: Save and run the application.
## PROGRAM:
Program to create and design an android application simple calculator using Intent.
### Developed by: SAHANA S
### Registration Number :212225040356

## AndroidMainfest.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android">

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Calculator">

        <activity
            android:name=".MainActivity"
            android:exported="true">

            <intent-filter>
                <action android:name="android.intent.action.MAIN"/>

                <category android:name="android.intent.category.LAUNCHER"/>

            </intent-filter>

        </activity>

    </application>

</manifest>
```
## MainActivity.java
```java
package com.example.calculator;

import android.os.Bundle;
import android.widget.Button;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    TextView tvExpression, tvResult;

    String currentInput = "";
    double firstNumber = 0;
    String operator = "";
    boolean isNewInput = true;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        tvExpression = findViewById(R.id.tvExpression);
        tvResult = findViewById(R.id.tvResult);

        // Number Buttons
        int[] numberButtons = {
                R.id.btn0, R.id.btn1, R.id.btn2, R.id.btn3, R.id.btn4,
                R.id.btn5, R.id.btn6, R.id.btn7, R.id.btn8, R.id.btn9
        };

        for (int id : numberButtons) {
            Button btn = findViewById(id);

            btn.setOnClickListener(v -> {

                if (isNewInput) {
                    currentInput = "";
                    isNewInput = false;
                }

                currentInput += btn.getText().toString();

                tvResult.setText(currentInput);

            });
        }

        // Operators
        findViewById(R.id.btnPlus).setOnClickListener(v -> setOperator("+"));
        findViewById(R.id.btnMinus).setOnClickListener(v -> setOperator("-"));
        findViewById(R.id.btnMultiply).setOnClickListener(v -> setOperator("*"));
        findViewById(R.id.btnDivide).setOnClickListener(v -> setOperator("/"));

        // Equals
        findViewById(R.id.btnEquals).setOnClickListener(v -> calculate());

        // Clear
        findViewById(R.id.btnClear).setOnClickListener(v -> clearCalculator());

    }

    private void setOperator(String op) {

        if (currentInput.isEmpty())
            return;

        firstNumber = Double.parseDouble(currentInput);
        operator = op;

        // Show expression
        tvExpression.setText(currentInput + " " + op);

        isNewInput = true;
    }

    private void calculate() {

        if (currentInput.isEmpty())
            return;

        double secondNumber = Double.parseDouble(currentInput);
        double result = 0;

        switch (operator) {

            case "+":
                result = firstNumber + secondNumber;
                break;

            case "-":
                result = firstNumber - secondNumber;
                break;

            case "*":
                result = firstNumber * secondNumber;
                break;

            case "/":

                if (secondNumber == 0) {
                    tvResult.setText("Error");
                    clearValues();
                    return;
                }

                result = firstNumber / secondNumber;
                break;
        }

        // Show completed expression
        tvExpression.setText(firstNumber + " " + operator + " " + secondNumber);

        if (result == (long) result) {
            tvResult.setText(String.valueOf((long) result));
            currentInput = String.valueOf((long) result);
        } else {
            tvResult.setText(String.valueOf(result));
            currentInput = String.valueOf(result);
        }

        isNewInput = true;
    }

    private void clearCalculator() {

        clearValues();

        tvExpression.setText("");
        tvResult.setText("0");
    }

    private void clearValues() {

        currentInput = "";
        firstNumber = 0;
        operator = "";
        isNewInput = true;

    }
}
```
## themes.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<resources xmlns:tools="http://schemas.android.com/tools">

    <style name="Theme.Calculator"
        parent="Theme.Material3.DayNight.NoActionBar">

        <item name="android:statusBarColor">@color/background</item>

        <item name="android:navigationBarColor">@color/background</item>

    </style>

</resources>
```
### string.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string name="app_name">Calculator</string>
    <string name="zero">0</string>
    <string name="error">Error</string>
</resources>
```
### output

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b7d33518-51a1-4826-b147-77fa96bb3b45" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/428b2273-9356-4083-848a-b9c36312846d" />


## RESULT
Thus a Simple Android Application create a simple calculator using Android Studio is developed and executed successfully.
