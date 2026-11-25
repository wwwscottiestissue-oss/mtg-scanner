# MTG Card Scanner

Scan Magic: The Gathering cards with your phone camera. The app identifies the card and its set, adds it to a spreadsheet (quantity goes up each time you scan the same card), and looks up NM and PL prices at TCGplayer, 401 Games and Face to Face Games.

| Name | Qty | TCGplayer NM / PL (USD) | 401 Games NM / PL (CAD) | Face to Face NM / PL (CAD) |
|------|-----|-------------------------|-------------------------|----------------------------|

## How it identifies the set

Cards printed since about 2020 have the set code and collector number in the bottom-left corner (for example `TRC` and `0183`). The app reads that text and looks up that exact printing on Scryfall, a free MTG database. The set symbols it shows are the same symbols as on the Keyrune site.

Older cards don't have that code. For those, the app reads the card name and shows every printing with its set symbol, and you tap the one that matches your card. You can also type a name in the search box.

## Two ways to run it (same app)

| | Android app (APK) | Web app in Chrome |
|---|---|---|
| Install | Sideload an APK once | Open a link, then "Add to Home screen" |
| TCGplayer | NM and PL, lowest listing | NM only (TCGplayer market price) |
| 401 Games / Face to Face | NM and PL, live | Shows an "open" link to that store's page (stores block websites from reading their prices) |

## Setup with a free GitHub account (no Android Studio needed)

1. Sign up at github.com and create a new **public** repository, e.g. `mtg-scanner`.
2. In the repo, click **Add file → Upload files** and drag in **everything inside this folder**, including the `.github` folder. Commit to `main`.
3. **Web app:** go to **Settings → Pages**, set **Source = GitHub Actions**, then go to **Actions → "Publish web app" → Run workflow**. Your app will be at `https://<your-username>.github.io/mtg-scanner/`. Open it on your phone in Chrome, then use ⋮ → **Add to Home screen**.
4. **Android app:** go to **Actions → "Build Android APK"**. When the run turns green (about 3–5 minutes), open it and download **MTG-Scanner-APK** under Artifacts. Unzip it to get `app-debug.apk`, copy it to your phone, and tap it to install. Android will ask you to allow installs from that source.

## Setup with Android Studio instead

Open this folder in Android Studio, let it sync, plug in your phone (with USB debugging on) and press **Run**.

## Using it

- **Start camera**, line the card up with the gold frame (the dashed boxes are the name bar and the set code corner), then tap **Scan card**. Good light and a flat card help a lot.
- Tick **Foil** before scanning foils. Foils are kept as separate rows and priced separately.
- After each scan, a bar at the bottom offers **Undo** and **Wrong card?** ("Wrong card?" lets you pick the right printing by its set symbol).
- Card names and quantities are editable in the table. Use **New sheet** for separate lists (binder, trade pile, …). The sheet name is editable.
- **Export CSV** opens in Excel or Google Sheets. In the Android app it saves to Downloads. **Copy** copies the sheet so you can paste it.
- Tap any price to open that card at that store. A number in brackets is how many the store has in stock. Struck-through prices mean the card is out of stock. "none" means the store doesn't list that printing.

## Notes

- 401 Games sells singles as NM / SP / MP. SP (slightly played) is shown in the PL column.
- TCGplayer prices are in USD. The Canadian stores are in CAD.
- Your sheets are saved on the phone, inside the app or browser. Clearing the browser or app data deletes them, so export a CSV now and then as a backup.
- The text reader (Tesseract) downloads about 10 MB the first time you scan.
- Store prices are read from the stores' public product data. If a store redesigns its site, that column may stop filling in until the matching code is updated.
