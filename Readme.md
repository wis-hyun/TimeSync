# 🌍 TimeSync
A real-time team scheduling app for international friend groups across different time zones.

---

## 🎯 Project Vision

Managing schedules across time zones is hard — especially when your friends are spread across Korea, Hawaii, California, and beyond.

**TimeSync** makes it effortless. Register your city, mark your availability, and instantly see the best overlapping times — all synced live with Firebase so everyone stays on the same page.

> No accounts, no installs. Just a shared team name and password.

---

## ✨ Features

### 🌐 World Clock
- Live clocks for all registered team members' cities
- Active hours (09:00–23:00 local time) highlighted in color
- Auto-updates every second

### 📅 Find a Time
- Create shared scheduling events with multi-date drag selection
- Availability heatmap — darker green = more people free
- Hover/click any slot to see **exactly who is available**
- **Best Times** panel: shows top overlapping slots ranked by availability
  - Only appears when **2+ people** have marked their availability
  - Gold / Silver / Bronze ranking with progress bars

### 🔄 Real-Time Sync
- Powered by Firebase Realtime Database
- All availability updates appear instantly for every team member
- No refresh needed

---

## 🤝 How It Compares

| Feature | Regular Scheduling Apps | 🌍 TimeSync |
|---|---|---|
| Time Zone Awareness | ⚠️ Manual conversion | ✅ Automatic UTC conversion |
| Real-Time Updates | ❌ Refresh required | ✅ Live Firebase sync |
| Team Access | ❌ Requires accounts | ✅ Shared team name + password |
| Availability Heatmap | ❌ Not available | ✅ Color-coded overlap view |
| Best Time Ranking | ❌ Not available | ✅ Ranked with participant names |

---

## 🏗️ Architecture

```
timesync-firebase.html          # Single-file app (HTML + CSS + JS)
│
├── 🎨 CSS (Styles)
│   ├── Light / Dark theme (system-aware)
│   ├── World Clock grid
│   ├── Heatmap + tooltip
│   └── Best Times ranking cards
│
├── 🧱 HTML (Structure)
│   ├── Login screen (name + team + password)
│   ├── World Clock panel
│   └── Find a Time panel
│       ├── Event list
│       ├── Create event (drag calendar picker)
│       ├── Availability heatmap
│       └── Best Times section
│
└── ⚙️ JavaScript (Logic)
    ├── Firebase Realtime Database integration
    ├── UTC ↔ Local time conversion
    ├── Heatmap rendering (slotCount + slotNames)
    ├── Drag calendar (mouse + touch)
    └── Best Times ranking logic
```

---

## 🔧 Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Vanilla HTML / CSS / JavaScript |
| Database | Firebase Realtime Database (Spark free tier) |
| Hosting | Netlify Drop (single file) |
| Time Zones | Browser `Intl` API (`toLocaleString` with `sv-SE`) |
| Auth | Team-based password stored in Firebase |

---

## 🚀 Quick Start

### 1. Deploy

Drag `timesync-firebase.html` to [Netlify Drop](https://app.netlify.com/drop) — no build step needed.

### 2. Set Up Firebase

1. Go to [Firebase Console](https://console.firebase.google.com/) → Create project
2. Enable **Realtime Database** (test mode)
3. Copy your Firebase config into the `firebaseConfig` object in the HTML:

```js
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  databaseURL: "https://YOUR_PROJECT-default-rtdb.firebaseio.com",
  projectId: "YOUR_PROJECT",
  storageBucket: "YOUR_PROJECT.firebasestorage.app",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

### 3. Use the App

1. Open the deployed URL
2. Enter your **name**, **team name**, and **team password**
3. Add your city to the World Clock
4. Create a scheduling event and drag to select dates
5. Click time blocks to mark your availability → hit **Save**
6. Share the URL + team credentials with your friends!

---

## 📖 Usage Example

```
Team name:  "hawaii-squad"
Password:   "aloha2026"

Members:
  · Sung      → Seoul, Korea     (UTC+9)
  · Hannah    → Honolulu, Hawaii (UTC-10)
  · Nolen     → Los Angeles, CA  (UTC-7)

Event: "First Meeting"
→ Heatmap shows overlapping slots in green
→ Best Times ranks top slots: "Tue, Oct 20 · 15:00 KST — 2/3 available"
```

---

## 🗺️ Roadmap

### Phase 1: Core ✅
- [x] Firebase real-time sync
- [x] Team-based login
- [x] World Clock with city registration
- [x] Availability heatmap
- [x] UTC-aware slot storage

### Phase 2: UX Improvements ✅
- [x] Slot tooltip (who is available)
- [x] Best Times ranking panel
- [x] Drag calendar date picker
- [x] Active hours highlighting (09:00–23:00)
- [x] Best Times visible only with 2+ participants

### Phase 3: Future Ideas
- [ ] Push notifications when team marks availability
- [ ] Google Calendar export
- [ ] Recurring event support
- [ ] Mobile app (PWA)

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add your feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License.

---

## 📞 Contact

- **Maintainer:** wis-hyun
- **Repository:** https://github.com/wis-hyun/timesync
- **Issues:** https://github.com/wis-hyun/timesync/issues

---

🌍 *Built for international friend groups who just want to find a time that works.*
