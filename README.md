# Vroom Vroom of Villainy

A top-5 F1 prediction league for qualifying, sprint qualifying, sprint and the Grand Prix, with a running season total. One HTML file, hosted free on GitHub Pages, with picks stored in a free Firebase database.

## 1. Create the database (Firebase, about 5 minutes)

1. Go to https://console.firebase.google.com and click **Create a project**. Any name works. You can turn Google Analytics off.
2. In the project, open **Build > Firestore Database > Create database**. Pick a location near you and start in **production mode**.
3. Open the **Rules** tab, replace everything with the rules below, and click **Publish**:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /league/{doc}  { allow read, write: if true; }
    match /picks/{doc}   { allow read, write: if true; }
    match /results/{doc} { allow read, write: if true; }
  }
}
```

4. Click the gear icon > **Project settings**. Under **Your apps**, click the **</>** (web) icon, give it a nickname, and register it. You don't need Firebase Hosting.
5. Copy the `firebaseConfig` values it shows you (apiKey, authDomain, projectId, and so on).

## 2. Add your config

Open `index.html` in any text editor. Near the top, fill in the `FIREBASE_CONFIG` block with the values from step 5 and save.

The Firebase web config isn't a secret, so it's fine for it to sit in a public repo.

## 3. Put it on GitHub Pages

1. Create a new repository on GitHub (for example `vroom-vroom-of-villainy`). It must be **public** for free Pages.
2. Click **Add file > Upload files**, drop in `index.html` (and this README if you like), and commit.
3. Go to **Settings > Pages**. Under **Build and deployment**, set Source to **Deploy from a branch**, then choose branch **main** and folder **/ (root)**, and click Save.
4. After a minute your league is live at `https://<your-username>.github.io/vroom-vroom-of-villainy/`. Send that link to the group.

## Using it

- The first person to open the link creates the league: add player names and an optional admin PIN.
- Everyone picks their name in **Picking as** (remembered on their device) and makes their top 5 for each session.
- After each session, anyone can tap **Enter results**. Points are scored instantly.
- The admin (whoever knows the PIN) can fill in or fix anyone's picks, edit the calendar, drivers and scoring, and bulk-import past weekends under **League setup**.

## A note on security

Anyone who has the link can read and change the league data. That's fine for a group of friends, but don't post the link publicly. The admin PIN keeps honest people honest; it isn't real security.
