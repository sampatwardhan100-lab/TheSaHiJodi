# #TheSaHiJodi · Our Notebook

A private notebook for Rahi & Sameer, started for our 4th wedding anniversary (26 November 2026).

**Open it:** https://sampatwardhan100-lab.github.io/TheSaHiJodi/

Only our two accounts can sign in, and after signing in it asks for our day.

## What's inside

- **Our story:** a timeline and a constellation of the moments that made us, with a photo for each one
- **Meet us:** a profile for each of us, with Instagram links
- **Our favourites:** songs, films, shows, food, places and more, plus our playlists
- **Our songs:** ForeverThing, Sata Janmanchi and our engagement video, playing inside the page
- **Best memory of every year:** from 2016 onwards, pinned on a map
- **Little things, in our words** and **our special places**
- **Our album:** any photo, any day
- **Games:** our quiz, “who's more likely to…” and “how well do you know me?” with a scoreboard
- **Open-when letters, reasons, love coupons and the date jar**
- **Our next chapter:** bucket list, promises and a time capsule
- **Our notebook:** a shared diary
- **My space:** a private area for each of us (private notes, surprise ideas, account)
- **Remember:** type anything the way you'd say it, and it gets sorted into the right place

Everything can be added and edited from inside the page. Tap **Edit** in the top bar, or **Remember**.

## How it works

- One file: `index.html`, hosted on GitHub Pages
- Sign-in and data: Firebase Authentication and Cloud Firestore (project `thesahijodi`)
- Our text and photos are stored in Firebase, not in this repo
- The Remember box can use Firebase AI Logic (Gemini) to fix typos and sort notes. Without it, the page sorts them with simple rules.

## Firestore rules

Shared things go in `couples/`, and each person's private space goes in `private/{email}`:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{db}/documents {
    function isUs() {
      return request.auth != null &&
        request.auth.token.email in ['OUR_EMAIL_1', 'OUR_EMAIL_2'];
    }
    match /couples/{doc=**} {
      allow read, write: if isUs();
    }
    match /private/{email}/{doc=**} {
      allow read, write: if isUs() && request.auth.token.email == email;
    }
  }
}
```

## Updating the page

Replace `index.html` with the new version (Add file → Upload files). GitHub Pages updates in a few minutes. The version number is shown at the bottom of the page, under **About**.

## Versions

- **v2.4**: My space, a private area for each of us; private notebook entries
- **v2.3**: Instagram on our profiles
- **v2.2**: “How well do you know me?” with a scoreboard
- **v2.1**: Our favourites and playlists
- **v2.0**: Everything editable in the page, the Remember box, album, coming up, backup
- **v1.2**: Our two accounts and full names
- **v1.1**: Sign-in, passcode, profiles, photos, notebook
- **v1.0**: The first anniversary page

Made with all my love · 26.11.2022 → forever
