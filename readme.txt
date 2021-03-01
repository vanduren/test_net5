Gebaseerd op:
https://www.youtube.com/watch?v=VIlDni8-iWM&ab_channel=SingletonSean
Publish met de .net publish commando (console).

Publish een WPF app mbv github actions (ci/cd workflow).

Doel: een online link naar de wpf app, die automatich wordt geupdate met een nieuwe release.

1. Maak git repo en push alles naar github.
2. Open map met projectbestand (csproj) en ga naar terminal:
3. Run: dotnet publish -c release
4. (of gebruik visual studio)
5. Voor een self contained package (inclusief dotnet versie) gebruik...
6. Run: dotnet publish -c release --self-contained
7. Dan krijg je een foutmelding. Zoek in google naar dotnet publish 
    https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-publish
    Ga naar runtime identifier catalog (platform). Dus te gebruiken: win-x64
8. Run: dotnet publish -c release --self-contained -r win-x64
9. Check dir en zie dat er veel files zijn. Dus alles in 1 file:
10. Run: dotnet publish -c release --self-contained -r win-x64 -p:PublishSingleFile=true

De github workflow:
1. Maak map ".git" aan in project met daarin de map "workflows"
2. Maak in workflows bestand aan (naam maakt niet uit extensie moet "yml" zijn)
3. Zie de inhoud en comments van de yml file
4. Zorg er wel voor dat de yaml op github ligt.
5. Maak een tag: git tag test/v0.0.1
6. Push de tag naar github: git push origin test/v0.0.1
7. Check of de workflow loopt.
8. Maak een release op github waar de single file kunnen uploaden
9. Voordat je gaat testen even het bestand (run-time-identifier) test.csproj
10. Zet daar: <RuntimeIdentifier>win-x64</RuntimeIdentifier> in de propertygroup
11. Vergeet niet weer git push
