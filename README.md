# WildSpot

## Funktionen
- Interaktive Fotospotkarte mit sechs Startpunkten und automatischen externen OSM-Naturorten (Schutzgebiete, Aussichtspunkte, Feuchtgebiete, Vogelbeobachtungshütten) im Rhein-Main-Gebiet
- Motivfilter, eigene Spots (mit Koordinaten), Favoriten und privates Beobachtungslogbuch
- Aktuelle Bewölkung, tiefe Wolken, Sichtweite, Nebelhinweis auf Modellbasis und Luftfeuchtigkeit sowie Sonnenauf- und -untergang des gewählten Spots (Open-Meteo)
- JSON-Backup und Import

## Datenquellen
OpenStreetMap-Karte via Leaflet, Naturorte über Overpass (OpenStreetMap) und Wetter von Open-Meteo. OSM-Orte sind landschaftliche Kandidaten, keine geprüfte Rangliste der besten Fotospots; Nebel wird aus Sichtweite und Wettercode interpretiert und ist keine sichere Messung vor Ort. Für die Karte muss eine Internetverbindung bestehen. Ausgangsorte/Koordinaten sind ungefähre Orientierungspunkte; keine garantierten Sichtungen. Bitte die Natur und Schutzgebiete respektieren.

## Installation über GitHub Pages

1. ZIP entpacken. **Für jede App ein eigenes GitHub-Repository** anlegen (öffentlich, wenn GitHub Pages kostenlos genutzt werden soll).
2. Den **Inhalt des entpackten App-Ordners** in das Repo-Root hochladen oder via Git pushen. Die versteckte `.github`-Struktur muss mit übernommen werden, falls vorhanden.
3. Unter **Repository → Settings → Pages** einstellen: für Market Pulse und Frankfurt Radar **Source: GitHub Actions**; bei den vier anderen **Deploy from a branch**, Branch `main`, `/(root)`.
4. Nach dem Deployment die bereitgestellte Pages-URL auf dem iPhone in Safari öffnen und unter Teilen **Zum Home-Bildschirm** wählen.
5. Falls Updates zunächst nicht sichtbar sind: Seite neu laden und ggf. den Homescreen-Link schließen und neu öffnen. Die Service-Worker-Datei nutzt bei Internetzugang eine Network-first-Strategie.

### Lokal ausprobieren

Im jeweiligen Ordner ausführen:

```sh
python3 -m http.server 8000
```

Dann `http://localhost:8000` im Browser öffnen. Für RSS-Apps muss zuvor das jeweilige `scripts/fetch_*.py` ausgeführt werden, um Online-Schlagzeilen abzurufen.

### Datenschutz

Persönliche Daten werden im lokalen Browser-Speicher gespeichert (bei Bildern IndexedDB). Es gibt keine Anmeldung und keine Synchronisierung. Der Quellcode eines öffentlichen GitHub-Repositorys ist öffentlich, **deine lokal eingegebenen Daten jedoch nicht im Repo enthalten**. Drittanbieter-Dienste für Karten, Wetter und RSS können übliche Verbindungsdaten erhalten. Import/Export von persönlichen Daten ist in den App-Einstellungen verfügbar (Bilder gesondert beachten).

### Technische Details

- Reines HTML/CSS/JavaScript, keine Build-Pipeline, keine bezahlten Dienste oder verpflichtenden API-Keys
- Responsiv für iPhone und Desktop, Hell-/Dunkelmodus, PWA-Manifest und Service Worker
- API-/Netzwerkzugriff erforderlich für aktuelle Feeds und externe Karten/Wetter
- **Prototypen:** vor produktivem Einsatz oder Veröffentlichung mit echten Daten bitte weitere Tests durchführen
