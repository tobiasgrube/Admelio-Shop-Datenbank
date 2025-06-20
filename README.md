# 📦 Anleitung zur Wiederherstellung einer .bak-Datei in SQL Server Management Studio (SSMS)

Diese Anleitung beschreibt Schritt für Schritt, wie Sie die `.bak`-Datei (SQL Server Backup) der AdmelioShop-Datenbank in **SQL Server Management Studio (SSMS)** einbinden und daraus eine funktionsfähige Datenbank wiederherstellen.

---

## ✅ Voraussetzungen

- SQL Server Management Studio (SSMS) ist installiert  
- Eine gültige `.bak`-Datei ist vorhanden (`AdmelioShop.bak`)  
- Sie verfügen über ausreichende Zugriffsrechte auf den Zielserver und den Speicherort der Datei  

---

## 🧭 Schritt-für-Schritt-Anleitung

### 1. SSMS starten und mit dem Datenbankserver verbinden
Öffnen Sie **SQL Server Management Studio** und stellen Sie eine Verbindung zu dem gewünschten SQL Server her (lokal oder remote).

---

### 2. Wiederherstellungsdialog öffnen
- Klicken Sie im **Objekt-Explorer** mit der rechten Maustaste auf den Knoten `Datenbanken`
- Wählen Sie anschließend **„Datenbank wiederherstellen…“**

---

### 3. Wiederherstellungsquelle auswählen
- Wählen Sie unter **Quelle** den Eintrag **„Gerät“**
- Klicken Sie rechts auf die Schaltfläche `...`
- Wählen Sie **„Hinzufügen“**, navigieren Sie zur `.bak`-Datei und bestätigen Sie mit **OK**

---

### 4. Ziel-Datenbankname festlegen
- Unter **Ziel** können Sie einen Namen für die wiederherzustellende Datenbank angeben, z. B. `AdmelioShopDB`
- Existiert bereits eine Datenbank mit diesem Namen, können Sie diese entweder überschreiben oder einen alternativen Namen vergeben

---

### 5. Wiederherstellungsoptionen prüfen
- Wechseln Sie zum Reiter **„Optionen“**
- Prüfen Sie insbesondere folgende Einstellungen:
  - `✓ Bestehende Datenbank überschreiben` (falls gewünscht)
  - Speicherorte der **Daten- und Log-Dateien** (`.mdf` / `.ldf`) ggf. anpassen

---

### 6. Wiederherstellung ausführen
- Klicken Sie auf **OK**, um den Wiederherstellungsprozess zu starten
- Der Fortschritt wird in der unteren Statusleiste von SSMS angezeigt

---

### 7. Erfolg kontrollieren
- Nach erfolgreicher Wiederherstellung erscheint die Datenbank im **Objekt-Explorer**
- Sie können nun Tabellen, Sichten und gespeicherte Prozeduren einsehen und verwenden

---

## 🛠️ Alternative: Wiederherstellung per T-SQL

```sql
RESTORE DATABASE AdmelioShopDB
FROM DISK = 'C:\Backups\AdmelioShopDB.bak'
WITH REPLACE,
     MOVE 'AdmelioShopDB_Data' TO 'C:\SQLData\AdmelioShopDB.mdf',
     MOVE 'AdmelioShopDB_Log' TO 'C:\SQLData\AdmelioShopDB_log.ldf';
