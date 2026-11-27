# Jarden mail

`mail.json` is the mailbox feed for every Jarden player. The game downloads it at launch and every 30 minutes:

https://raw.githubusercontent.com/toast122/jarden-mail/main/mail.json

## Sending a letter

1. Add a letter to the `mail` list in `mail.json` (copy an existing one).
2. Give it a **new, unique `id`** and never reuse an old one: claims and "read" marks are saved by id.
3. Check it in Unity: **Jarden → Mail → Check a feed file...**
4. Commit and push (GitHub Desktop). Players get it within about 30 minutes; GitHub can take a few extra minutes to serve the new file.

## Letter fields

| Field | Meaning |
|---|---|
| `id` | Unique name, e.g. `xmas-2026` (required) |
| `from` | Sender shown on the letter (default "The Gardener") |
| `title` | Headline (required) |
| `body` | The message. `\n` for a new line; `<b>bold</b>`, `<i>italic</i>`, `<color=#C2410C>color</color>` work |
| `date` | `yyyy-MM-dd`: shows from this day (empty = right away) |
| `expires` | `yyyy-MM-dd`: last day it shows (empty = never) |
| `pinned` | `true` keeps it at the top |
| `moonstones` | Gift (max 5,000 per letter) |
| `seeds` | Gift, whole Seeds (max 1 billion) |
| `dewMinutes` | Gift: minutes of the player's current dew production (max 1,440) |
| `decor` | Gift: a decoration id from the Garden catalog |
| `action` | Optional button: `open:moonshop`, `open:boosts`, `open:garden`, `open:quests`, `open:calendar`, `open:upgrades`, `open:seeds`, `open:stats`, or `url:https://...` |
| `actionLabel` | Text on that button |

Every gift can be claimed once per player. Removing a letter from the file removes it from everyone's mailbox.

## Example

```json
{
  "id": "xmas-2026",
  "title": "Merry Christmas!",
  "body": "The whole garden is glowing tonight.\nHere's a little something under the tree.",
  "date": "2026-12-24",
  "expires": "2026-12-31",
  "moonstones": 100,
  "action": "open:moonshop",
  "actionLabel": "Visit the Moon Shop"
}
```
