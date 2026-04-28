# Ex.No:2a Develop program to create a text field and a button “Navigate”. When you enter “www.gmail.com” and press navigate button it should open google page using Implicit Intents.


## AIM:

To create a navigate button using Implicit Intent to display the gmail page using Android Studio.

## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

1: Open Android Stdio and then click on File -> New -> New project.

2: Then type the Application name as ImplicitIntent and click Next.

3: Then select the Minimum SDK as shown below and click Next.

4: Then select the Empty Activity and click Next. Finally click Finish.

5: Design layout in activity_main.xml.

6: Display message give in MainActivity file.

7: Save and run the application.


## PROGRAM:
```
/*
Program to print the text “Implicitintent”.
Developed by: Sri Yaline R
Registeration Number : 212224040325
*/


MainActivity.Java

package com.example.myapplication;

import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    private EditText urlEditText;
    private Button btnOpenUrl;


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        urlEditText = findViewById(R.id.urlEditText);
        btnOpenUrl = findViewById(R.id.navigateButton);


        // Implicit Intent 1: Open a Web Browser
        btnOpenUrl.setOnClickListener(v -> {
            String url = urlEditText.getText().toString().trim();
            if (url.isEmpty()) {
                urlEditText.setError(getString(R.string.error_empty_url));
                return;
            }
            if (!url.startsWith("http://") && !url.startsWith("https://")) {
                url = "https://" + url;
            }

            Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse(url));
            try {
                startActivity(intent);
            } catch (Exception e) {
                Toast.makeText(this, "No browser found", Toast.LENGTH_SHORT).show();
            }
        });

    }
}



activity_main.xml

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="20dp"
    android:gravity="center">

    <EditText
        android:id="@+id/urlEditText"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="@string/url_hint"
        android:inputType="textUri"
        android:padding="10dp"
        android:textSize="18sp"/>

    <Button
        android:id="@+id/navigateButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/open_url"
        android:padding="12dp"
        android:textSize="18sp"
        android:layout_marginTop="20dp"/>

</LinearLayout>


AndroidManifest.xml

<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <uses-permission android:name="android.permission.INTERNET" />

    <queries>
        <intent>
            <action android:name="android.intent.action.VIEW" />
            <category android:name="android.intent.category.BROWSABLE" />
            <data android:scheme="http" />
        </intent>
        <intent>
            <action android:name="android.intent.action.VIEW" />
            <category android:name="android.intent.category.BROWSABLE" />
            <data android:scheme="https" />
        </intent>
    </queries>

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.MyApplication">

        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

    </application>

</manifest>

```

## OUTPUT


<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/a8816566-8cdf-493b-aee1-01ad0dc0e5d9" />

<img width="1920" height="1200" alt="Screenshot 2026-04-28 081625" src="https://github.com/user-attachments/assets/38f0af60-dc32-4171-82e1-a57ff3273cfe" />


## RESULT
Thus a Simple Android Application create a navigate button using Implicit Intent to display the gmail page using Android Studio is developed and executed successfully.


