# Daily maintenance

A scheduled Claude task runs this checklist every morning (America/New_York).

## Sources, in order
1. **Daily Messages** — the newest "Daily Messages for …" emails in Gmail (from message@williams.edu) since the last run. Open every linked `events.williams.edu/event/…` page, not only the one-line summary, and look for food, snacks or drinks anywhere in the full description (e.g. "followed by dinner", "light lunch will be served").
2. **Williams calendar** — `events.williams.edu/wp-json/tribe/events/v1/events/?start_date=…&end_date=…&per_page=50` for the next 8 weeks, including entries marked `hide_from_listings`. The site is behind a Cloudflare check that blocks GitHub Actions and cloud fetchers; use the built-in browser on Leyla's computer, which passes it.
3. **Other email** — club and department newsletters, Social Calendar, Muslim Life, SMAB Weekly, WOC, '68 Center, Davis Center, Record Recap, etc.
4. **Department websites and news feeds** — department event/news pages and the Williams Record.
5. **Club Instagram accounts** — best effort; Instagram usually requires a sign-in.

## Rules
- Only list food that attendees get free. Skip "$5 lunch", "bring your own", "for purchase".
- Never invent a time, place or food. Leave a field out if the source doesn't say.
- Staff-only or faculty-only events get `"eligibility": "Specific group"`, or are skipped if students can't attend.
- Add new items to `data/maintainer-listings.json` → `events`. Remove a wrong or duplicate listing by adding `{title, date}` to `cancellations` (titles must match the published title).
- Cancel weekly repeats that fall in breaks (Thanksgiving, winter break, spring break).
- No email addresses, phone numbers, Gmail links or URLs in titles/food/location; `url` must be an official Williams page.
- Run `npm test` before pushing to `main`. The push triggers the Pages build.
