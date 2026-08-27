# Pawiro Home V6

Pawiro Home V6 is a local-first PWA prototype focused on intelligent household coordination. It builds on the V5 foundation and adds workflows, dependencies, priority planning, energy-aware recommendations, household memory, inventory, smart shopping, AI knowledge recommendations, intelligent reminders concepts, task handover/snooze concepts, and in-app voice commands.

## 1. What is included

- Home dashboard with "What should I do now?"
- 15 / 30 / 60 minute planning and energy matching
- Priority queue with "Why?" explanations
- Reusable household workflows with steps, triggers and follow-ups
- Ready / Waiting / Blocked / Complete workflow states
- Admin-style AI household knowledge recommendations requiring approval
- Oven-use logging through voice to support future dynamic maintenance recommendations
- In-app voice recognition using the browser Speech Recognition API where supported
- "Hey Pawiro" as the proposed voice phrase; this V6 prototype listens after pressing Start Listening
- Meals, recipes and recipe-to-shopping integration
- Shared shopping list and low-stock inventory suggestions
- Household balance analysis without competitive ranking
- Family profiles and profile photo/camera interface
- Calendar with day/week/month/year views
- Bin schedule foundation
- Tablet / Always-On dashboard
- Local persistence with localStorage
- PWA manifest and service worker
- Supplied Pawiro Home logo
- No external icon/font dependency and no garbled Unicode icon strings

## 2. Important: opening the files is NOT the full PWA test

You can double-click `index.html` to inspect the interface, but `file://` is not the correct way to test PWA installation or service-worker behaviour.

For a proper PWA test, serve the folder over HTTPS.

## 3. Easiest HTTPS test: Netlify

1. Extract the ZIP.
2. Open Netlify Drop: https://app.netlify.com/drop
3. Sign in if requested.
4. Drag the extracted `Pawiro_Home_V6` folder into the drop area.
5. Netlify will publish it with an HTTPS `https://....netlify.app` address.
6. Open that address on Android Chrome, iPhone/iPad Safari, tablet and desktop.
7. On Android Chrome, use the browser menu and choose Install app / Add to Home screen when offered.
8. On iPhone/iPad Safari, use Share → Add to Home Screen.
9. Launch the installed Pawiro Home icon and test it independently from the browser tab.

## 4. Local development test

If you have Python installed on a computer:

```bash
cd Pawiro_Home_V6
python -m http.server 8080
```

Then open:

`http://localhost:8080`

This is useful for functional testing on the same computer, but it is not a normal remote HTTPS deployment. For testing installation on a phone/tablet, use the HTTPS deployment method above.

## 5. PWA checks

After the HTTPS site loads:

- Confirm the Pawiro Home logo appears.
- Confirm the page can be installed.
- Close the browser tab and launch the installed app.
- Load the app once while online.
- Temporarily disable internet and test whether cached app files still open.
- Reconnect and refresh after testing.

Browser wording for installation and offline behaviour can vary by operating system and browser.

## 6. V6 intelligence prototype

### What Should I Do Now?

Choose 15, 30 or 60 minutes and Low/Medium/High energy. The prototype ranks tasks using priority, due date, workflow readiness, effort and time fit.

### Workflows

Example workflow chains included:

- Dishwasher: load → start → wait → empty → put away
- Laundry: load → start → wait → empty → fold → put away
- Bin collection: take out → collection → bring back

Use **Workflows** to inspect the chains or create your own reusable workflow. Steps can include a trigger and estimated duration.

### AI household knowledge

The prototype includes an Admin approval screen for recommendations such as oven-cleaning frequency. It deliberately does not pretend that a prototype has live web research. The production architecture should connect this screen to a web/manufacturer knowledge service and show sources before Admin approval.

### Voice

Press the microphone button and choose Start Listening. Supported browsers can recognise speech. Example phrases:

- "Hey Pawiro, I put pizza in the oven."
- "Hey Pawiro, start dishwasher."
- "Hey Pawiro, start laundry."
- "Hey Pawiro, I have 30 minutes and low energy."

The prototype records oven-use events and can start matching workflows. A true always-listening wake word while the app is closed is an OS/native-app capability and is therefore reserved for a later connected version.

## 7. Data model direction

V6 uses IDs for members, tasks, workflows, inventory, recipes and events so the prototype can later map to a cloud database. Current data is stored locally in the browser with `localStorage`.

A production version should replace local persistence with authenticated cloud storage and real-time synchronisation.

## 8. Council/bin integration

V6 contains the bin schedule model and calendar/dashboard surfaces. A production connector should resolve postcode → council → address/property/UPRN where available and then retrieve the property's actual collection dates. The prototype does not claim to have live council data.

## 9. Browser compatibility

Modern Chrome/Edge/Safari/Firefox are recommended. Voice recognition support varies by browser. Camera/profile photo input uses the normal device file/camera picker and requires permission.

## 10. Reset demo data

Use Settings → Reset V6 demo to clear local V6 data and reload the original demo state.
