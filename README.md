# 🔨 Szalagfűrés Adatbázis Kezelő

Egy teljes webes alkalmazás szalagfűrészes adatok kezeléséhez, bejelentkezéssel és JSON-alapú adattárolással.

## ✨ Funkciók

- 🔐 **Biztonságos bejelentkezés** (JWT token alapú)
- 📝 **Adatbeviteli forma** 8 mezővel
- 💾 **JSON-alapú adattárolás**
- 📊 **Adatok megtekintése táblázatban**
- 📥 **JSON importálás/exportálás**
- 🗑️ **Rekordok törlése**
- 📱 **Reszponzív design**

## 🚀 Telepítés

### Előfeltételek
- Node.js (v14 vagy újabb)
- npm

### Lépések

1. **Repository klónozása**
```bash
git clone https://github.com/zolauto/szalagfures-adatbazis.git
cd szalagfures-adatbazis
```

2. **Függőségek telepítése**
```bash
npm install
```

3. **Szerver indítása**
```bash
npm start
```

A szerver elindul a `http://localhost:3000` címen.

## 🔑 Admin Bejelentkezés

### Első Bejelentkezés

Amikor először indítod a szerver, nincs admin fiók létrehozva. A bejelentkezési oldalon (`http://localhost:3000/login.html`) egy gomb jelenik meg az első admin fiók létrehozásához.

**Automatikusan generált admin jelszó:**
```
Felhasználónév: admin
Jelszó: SzalagFures2025!Secure
```

> ⚠️ **Fontos:** Az első bejelentkezés után **azonnal módosítsd a jelszót**!

### Jelszó Módosítása

Bejelentkezés után az adatbeviteli oldalon találsz egy `Jelszó Módosítása` gombot, ahol megváltoztathatod a jelszavad.

## 📁 Mappastruktúra

```
szalagfures-adatbazis/
├── server.js              # Express szerver
├── package.json           # Függőségek
├── .env.example          # Környezeti változók sablonja
├── .gitignore            # Git ignoráláshoz
├── public/
│   ├── login.html        # Bejelentkezési oldal
│   └── index.html        # Adatbeviteli oldal
└── data/
    ├── users.json        # Felhasználók (gitignorálva)
    └── records.json      # Adatrekordok (gitignorálva)
```

## 🔌 API Végpontok

### Autentikáció

#### POST `/api/login`
Bejelentkezés

**Request:**
```json
{
  "username": "admin",
  "password": "jelszó"
}
```

**Response:**
```json
{
  "token": "eyJhbGc...",
  "user": {
    "username": "admin",
    "role": "admin"
  }
}
```

#### POST `/api/change-password`
Jelszó módosítása (JWT szükséges)

**Headers:**
```
Authorization: Bearer TOKEN
```

**Request:**
```json
{
  "oldPassword": "régijelszó",
  "newPassword": "újjelszó"
}
```

### Rekordok

#### GET `/api/records`
Összes rekord lekérése

#### POST `/api/records`
Új rekord hozzáadása

**Request:**
```json
{
  "diameter": "D38",
  "material": "S255",
  "timeSec": "133",
  "beltSpeed": 60,
  "feed": 3.5,
  "current": 1.58,
  "partNumber": "K10763",
  "shelf": "E3"
}
```

#### PUT `/api/records/:id`
Rekord frissítése

#### DELETE `/api/records/:id`
Rekord törlése

### Admin

#### GET `/api/admin/users`
Felhasználók listája (csak admin)

#### POST `/api/admin/create-user`
Első admin fiók létrehozása

## 🔒 Biztonsági Megjegyzések

1. **Környezeti változók:** `.env` fájlban tárolod a `JWT_SECRET`-et
2. **Jelszavak:** bcrypt-tel hasheltetnek
3. **Tokenek:** JWT-vel kezeltetnek 24 órás lejárattal
4. **CORS:** Bekapcsolt a fejlesztéshez

## 📊 Adatformátum

Egy típikus rekord JSON-ben:

```json
{
  "id": "1721490000000",
  "diameter": "D38",
  "material": "S255",
  "timeSec": "133",
  "beltSpeed": 60,
  "feed": 3.5,
  "current": 1.58,
  "partNumber": "K10763",
  "shelf": "E3",
  "createdAt": "2025-07-21T10:30:00.000Z",
  "createdBy": "admin"
}
```

## 🛠️ Fejlesztéshez

### Logok megtekintése
```bash
npm start
```

### Szerver újraindítása
Nyomj `Ctrl+C` majd `npm start`

### Adatok törlése
A `data/` mappában lévő JSON fájlokat lehet kézzel szerkeszteni vagy törölni.

## 📝 Licenc

MIT

## 👤 Szerző

- **zolauto** - https://github.com/zolauto
