# Two Maids Bellevue — Schedule System v2

## Files

```
admin/
  index.html        ← PRIVATE — open locally, never upload

viewer/
  index.html        ← Upload to GitHub Pages (once, never changes)
  schedules.json    ← Upload to GitHub EVERY WEEK (this is the only file that changes)

README.md
```

---

## One-Time GitHub Setup (~10 minutes)

### 1. Create a public repository
- github.com → **+** → **New repository**
- Name: `schedule`  |  Visibility: **Public**  |  Check "Add a README"  →  **Create**

### 2. Upload viewer files
- **Add file → Upload files**
- Upload both `viewer/index.html` and `viewer/schedules.json`
- Commit to main

### 3. Enable GitHub Pages
- **Settings → Pages → Source:** Deploy from branch
- Branch: `main` / Folder: `/ (root)` → **Save**
- Wait ~60 seconds

### 4. Configure the viewer (edit index.html on GitHub)
- Open `index.html` in your repo → click the **pencil** icon
- Find this line:
  ```
  var JSON_URL = params.get('src') || 'SCHEDULES_JSON_URL';
  ```
- Replace `SCHEDULES_JSON_URL` with:
  ```
  https://raw.githubusercontent.com/vlicaros/TwoMaidsBellevueWeeklySchedule/main/schedules.json
  ```
- **Commit changes**

### 5. Set base URL in admin tool
- Open `admin/index.html` locally
- Go to **Step 2** → paste your GitHub Pages URL:
  ```
  https://vlicaros.github.io/TwoMaidsBellevueWeeklySchedule
  ```

---

## Send Permanent Links to Cleaners (send ONCE, never again)

```
https://vlicaros.github.io/TwoMaidsBellevueWeeklySchedule/?cleaner=megan
https://vlicaros.github.io/TwoMaidsBellevueWeeklySchedule/?cleaner=nick
https://vlicaros.github.io/TwoMaidsBellevueWeeklySchedule/?cleaner=tish
https://vlicaros.github.io/TwoMaidsBellevueWeeklySchedule/?cleaner=loreina
https://vlicaros.github.io/TwoMaidsBellevueWeeklySchedule/?cleaner=vance
```

Cleaners bookmark their link. That's it. They never need a new one.

---

## Weekly Workflow (~3 minutes every Monday)

```
1. Go to gataware.com/TwoMaidsBellevueWeeklySchedule/ while logged in
2. Click the bookmarklet → JSON copies to clipboard
3. Open admin/index.html locally
4. Paste JSON → click "Split into Cleaner Schedules"
5. Click "Download schedules.json"
6. Go to github.com → your schedule repo
7. Add file → Upload files → drag schedules.json → Commit
8. Done. Cleaners refresh their page and see the new schedule.
```

No new links. No texting links. Just upload one file.

---

## How it works

- The **viewer page** is a static HTML file that reads `?cleaner=name` from the URL
- It fetches `schedules.json` from GitHub each time it loads
- `schedules.json` contains all cleaners' data for the current week
- When you upload a new `schedules.json`, every cleaner's page updates automatically
- Links are short and permanent: `.../?cleaner=megan` — no data in the URL
