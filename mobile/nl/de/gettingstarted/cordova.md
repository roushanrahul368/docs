---

copyright:
  years: 2015, 2016

---
<!-- Attribute definitions -->
{:codeblock: .codeblock}

# Einführung in das Beispiel 'Hello Bluemix for Cordova'
{: #gettingstarted-cordova}
Letzte Aktualisierung: 27. Mai 2016
{: .last-updated}

Wenn Sie mit einer neuen Cordova-Anwendung arbeiten möchten, können Sie die App 'HelloWorld' verwenden. Diese App zeigt, wie Sie ohne Authentifizierung eine Verbindung von einer mobilen App zu Ihrem {{site.data.keyword.Bluemix}}-Back-End herstellen können. Für die App ist das SDK bereits installiert. Wenn Sie bereit sind, können Sie die spezifischen Bibliotheken abrufen, die Sie in Ihrer App verwenden möchten.

1. Erstellen Sie Ihr mobiles Back-End in {{site.data.keyword.Bluemix_notm}}.

	1. Klicken Sie im Abschnitt mit den Boilerplates im {{site.data.keyword.Bluemix_notm}}-Katalog auf 'MobileFirst Services Starter'.
	1. Geben Sie einen Namen und einen Host für Ihre App ein und klicken Sie auf **Erstellen**.
	1. Klicken Sie auf **Fertigstellen**.

2. Rufen Sie das Projekt aus GitHub ab. Sie können zum Abrufen des Projekts den Befehl 'git clone' verwenden. Öffnen Sie auf Ihrem Computer das Terminal und geben Sie den folgenden Befehl ein:

	```Bash
	git clone https://github.com/ibm-bluemix-mobile-services/bms-samples-cordova-helloworld
	```

3. Führen Sie in Ihrem Projektverzeichnis die folgenden Befehle aus, um die Android- und die iOS-Plattformumgebungen hinzuzufügen:

	### Android
	{: #cordova-android-run}

	```Bash
	cordova platform add android
	```

	### iOS
	{: #cordova-ios-run}

	```Bash
	cordova platform add ios
	```

4. Fügen Sie mithilfe des folgenden Befehls das Cordova-Plug-in hinzu:

	```Bash
	cordova plugin add ibm-mfp-core
	```

5. Konfigurieren Sie das Beispiel 'HelloWorld'.

	* Wechseln Sie in das Verzeichnis, in dem Sie das Projekt geklont haben.
	* Öffnen Sie die Datei *&lt;Verzeichnis Ihrer App&gt;*/www/js/index.js und ersetzen Sie *&lt;APPLICATION_ROUTE&gt;* und *&lt;APPLICATION_ID&gt;* durch Ihre Bluemix-Anwendungs-ID und Ihre Routewerte.

		**Anmerkung:** Stellen Sie sicher, dass Ihre Route das https-Protokoll sicher verwendet.

		```Javascript
		// Bluemix credentials
		route: "<APPLICATION_ROUTE>",
		GUID: "<APPLICATION_GUID>",
		```

6. Konfigurieren Sie Ihre Cordova-App für iOS. Für die Android-Plattform ist keine zusätzliche Konfiguration erforderlich.

	### iOS
	{: #cordova-ios-configure}
  Konfigurieren Sie Ihr Xcode-Projekt zur Vermeidung von Buildfehlern wie folgt.

	1. Verwenden Sie die neueste Version von Xcode, um Ihre Datei `xcode.proj` im Verzeichnis *&lt;App-Name&gt;*/platforms/ios zu öffnen.

		**Wichtig:** Wenn Sie eine Nachricht erhalten, in der Sie dazu aufgefordert werden, eine Konvertierung in die neueste Swift-Syntax durchzuführen, klicken Sie auf **Abbrechen**.

	2. Navigieren Sie zu **Build Settings > Swift Compiler - Code Generation > Objective-C Bridging Header** und fügen Sie den folgenden Pfad hinzu:

		```
		<your_project_name>/Plugins/ibm-mfp-core/Bridging-Header.h
		```

	3. Navigieren Sie zu **Build settings > Linking > Runpath Search Paths** und fügen Sie die folgenden Frameworks-Parameter hinzu:

		```
		@executable_path/Frameworks
		```

7. Erstellen Sie das Beispiel auf Ihrem mobilen Emulator oder Ihrem mobilen Gerät und führen Sie es aus.

  ### Android
  {: #cordova-android-build}
	1. Erstellen Sie mithilfe des folgenden Befehls die Cordova-App:

    **Wichtig:** Bevor Sie Ihr Projekt in Android Studio öffnen, müssen Sie zunächst Ihre Cordova-Anwendung über die Cordova-CLI (Befehlszeilenschnittstelle) erstellen. Ansonsten kommt es zu Buildfehlern.

	```Bash
	cordova build android
	```

	2. Führen Sie die Beispiel-App in Android Studio aus.

  ### iOS
  {: #cordova-ios-build}
  1. Erstellen Sie die Cordova-App in Xcode.

    **Tipp:** Die Erstellung in Xcode bietet weitere Optionnen, z. B. Debugging und Projektkonfiguration.

  2. Führen Sie die Beispiel-App in Xcode aus.

Es wird eine eine Anwendung mit einer einzelnen Ansicht mit der Schaltfläche **PING BLUEMIX** angezeigt. Wenn Sie die Schaltfläche antippen, testet die Anwendung die Verbindung zwischen dem Client und der {{site.data.keyword.Bluemix_notm}}-Back-End-Anwendung. Die Verbindung wird mithilfe der Anwendungsroute getestet, die Sie in der Datei `index.js` angegeben haben.

<!--
![Hello World application successfully connected to Bluemix](images/yayconnected.jpg "Figure 1. Hello World application successfully connected to Bluemix")
-->

  Wenn Sie in Android Studio erfolgreich eine Verbindung zwischen der mobilen App und {{site.data.keyword.Bluemix_notm}} hergestellt haben, wird die folgende Nachricht angezeigt:
  `Yay! You are connected`
  {: screen}


<!--![Hello World application not connected to Bluemix](images/bummer_android.jpg "Figure 2. Hello World application not connected to Bluemix")-->

Falls die Verbindung fehlschlägt, wird folgende Nachricht angezeigt:
  `Bummer. Something went wrong`
  {: screen}
   
Sie finden dort auch weitere Informationen zu dem Fehler. Sie können die folgenden Punkte prüfen, um Ihren Fehler zu beheben:

- Überprüfen Sie, dass Sie die Werte für die Route und die GUID ordnungsgemäß eingefügt haben.
- Ziehen Sie das Xcode- oder das Android-Debugprotokoll zurate.
- Überprüfen Sie den Status Ihrer App in {{site.data.keyword.Bluemix_notm}}.

## Nächste Schritte:
{: #next}
Informationen zum Abrufen des SDKs und zum Integrieren in Ihre mobile App finden Sie in:
* [Mobile Client Access: Cordova-Plug-in einrichten](../../services/mobileaccess/getting-started-cordova.html)
* [Push Notifications: Cordova-Plug-in einrichten](../../services/mobilepush/enablepush_cordova.html#setup_sdk_cordova)

# Zugehörige Links

## Beispiele
   * [Hello Bluemix (Cordova)](https://github.com/ibm-bluemix-mobile-services/bms-samples-cordova-helloworld)

## SDK
   * [bms-clientsdk-cordova-core](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-core)

<!--## api
   * [Core API](https://www.{DomainName}/docs/api/content/api/mobilefirst/cordova/core-api-doc/overview-summary.html)
-->
