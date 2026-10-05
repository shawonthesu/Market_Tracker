<h1 align="center">Market Tracker</h1>

<p align="center">
  A market and shopping list tracker with quantities, prices and discounts.<br>
  Log in once and your list follows you from your phone to your computer.
</p>

<p align="center">
  <a href="https://shawonthesu.github.io/Market_Tracker/"><b>Open the live app</b></a>
</p>

<p align="center">
  <img alt="HTML, CSS and JavaScript" src="https://img.shields.io/badge/web-HTML%20%7C%20CSS%20%7C%20JS-3a2314">
  <img alt="Supabase" src="https://img.shields.io/badge/backend-Supabase-3ecf8e">
  <img alt="Python Tkinter" src="https://img.shields.io/badge/desktop-Python%20%7C%20Tkinter-3776ab">
  <img alt="Hosted on GitHub Pages" src="https://img.shields.io/badge/hosted%20on-GitHub%20Pages-555">
</p>

---

## Screenshots

### Desktop

<p align="center">
  <img src="https://github.com/user-attachments/assets/5c81d946-9b5b-44ee-ae48-b95cf4f42e76" alt="Market Tracker on desktop, item list with total" width="800">
</p>
<p align="center">
  <img src="https://github.com/user-attachments/assets/be054fa8-598d-4ac1-88ba-779ce71019d7" alt="Market Tracker on desktop, add item popup" width="800">
</p>

### Mobile

<p align="center">
  <img src="https://github.com/user-attachments/assets/22e588a4-06d7-436f-9a08-757c7ce5eaeb" alt="Mobile view, item list" width="240">
  &nbsp;&nbsp;
  <img src="https://github.com/user-attachments/assets/36419294-d97d-49ff-958a-3f3bfda8dc23" alt="Mobile view, total bar" width="240">
</p>

## Try it on your phone

<p align="center">
  <img width="200" height="200" alt="Try it QRcode " src="https://github.com/user-attachments/assets/59a5de12-805c-4d8e-ace8-519470221792" /><br>
  <sub>Scan to open the app</sub>
</p>

## Features

| | |
|---|---|
| **Items** | Add, edit and delete items with a name, details, quantity, unit and unit price. Tick items off as bought. |
| **Discounts** | A percentage or fixed ₹ amount on any item, plus a discount on the whole bill. |
| **Totals** | Live subtotal, savings and final total, with Indian digit grouping (₹1,00,000.00). |
| **Accounts** | Email sign up and login. Each person sees only their own list. |
| **Cloud sync** | The list is stored in a database, so every device shows the same items. |
| **Safe to use** | Undo after a delete or a clear, and checks for empty names, zero quantities, negative prices and oversized discounts. |
| **Mobile friendly** | Large touch targets and a bottom bar that always shows the total. |

## How the total is worked out

1. Line total = quantity × unit price
2. Item discount = a percentage or fixed amount, never more than the line total
3. Subtotal = the sum of all line totals after item discounts
4. Bill discount = a percentage or fixed amount, never more than the subtotal
5. **Total = subtotal − bill discount**

## How it works

```mermaid
flowchart LR
  A["Browser or phone<br/>index.html on GitHub Pages"] -- "login and queries" --> B[("Supabase<br/>Auth + Postgres")]
  B -- "Row Level Security:<br/>only your own rows" --> A
```

The web app is a single static file with no build step. It talks to Supabase directly from the browser. Access control is done in the database with Row Level Security, so a logged-in user can only read and change their own rows.

## Tech stack

| Part | Technology |
|---|---|
| Web app | HTML, CSS and vanilla JavaScript in one file |
| Database and login | [Supabase](https://supabase.com) (Postgres, Auth, Row Level Security) |
| Hosting | GitHub Pages |
| Desktop app | Python 3 with Tkinter, standard library only |
| Look | Crumpled paper background, dark brown text, [Doto](https://fonts.google.com/specimen/Doto) font |


## Python desktop app

A standalone desktop version with the same look. It saves your list locally to `~/.market_tracker.json` and does not use the cloud database.

```bash
python3 market_tracker.py
```

It needs Python 3 with Tkinter. If Tkinter is missing, the script tries to install it with your system package manager. On Fedora you can also run `sudo dnf install python3-tkinter`.

**Doto font (optional):** Tkinter only uses installed fonts, so without it the app falls back to a monospace font. To install Doto:

```bash
mkdir -p ~/.local/share/fonts
cp Doto-*.ttf ~/.local/share/fonts/
fc-cache -f
```

## Project structure

```
Market_Tracker/
├── index.html             # Web app (HTML, CSS, JavaScript, Supabase)
├── market_tracker.py      # Python desktop app (Tkinter)
├── assets/
└── README.md
```

## Roadmap

- [x] Web app with discounts and totals
- [x] Mobile layout
- [x] Accounts and cloud sync with Supabase
- [ ] Sync the Python desktop app with the same database
- [ ] Work offline and sync when the connection returns
- [ ] Categories, search and export
