# ⏳ Simple Calendar

A lightweight edition of [World Calendar](https://github.com/wertyqazx/ai-dungeon-world-calendar) for AI Dungeon. Keep track of your adventure's date and season, skip time, and keep the AI aware of the passage of time.

## Features

- Persistent date and automatic seasonal tracking (Northern Hemisphere calendar seasons).
- Time skips in days, weeks, months, and years, including combined durations.
- Overnight transitions, confirmation for long skips, and undo.
- Manual date editing and configurable start date, era, and auto-skip limit.
- Optional Inner Self v1.0.2 and Auto-Cards v1.1.3, both disabled by default.

Unlike World Calendar, Simple Calendar does not track weather, locations, travel, holidays, or scheduled events. Ordinary story actions do not advance the calendar automatically.

## Installation

Open your scenario's scripting editor in AI Dungeon and paste each file from the [scripts/](scripts/) folder into its corresponding tab:

| File | Script tab |
| --- | --- |
| [`library.js`](scripts/library.js) | Library |
| [`input.js`](scripts/input.js) | Input |
| [`context.js`](scripts/context.js) | Context |
| [`output.js`](scripts/output.js) | Output |

Save the scripts and start a new adventure. This edition already includes Inner Self and Auto-Cards; do not install separate copies on top of the bundled scripts.

## Commands

Enter commands as **Story** actions.

| Command | Description |
| --- | --- |
| `:date` | Display the current date and season. |
| `:skip night` | Advance to the next morning. |
| `:skip 5 days` | Advance five days. |
| `:skip 2 weeks` | Advance two weeks. |
| `:skip 3 months` | Advance three months. |
| `:skip 1 year` | Advance one year. |
| `:skip 1 year 2 months 3 days` | Combine units. |
| `:yes` / `:no` | Confirm or cancel a pending skip. |
| `:undo` | Revert the latest skip within three actions. |
| `:help` | Show command help. |

Skips of seven days or fewer execute immediately by default. Longer skips require confirmation.

## Configuration

Edit the `WorldCalendarSettings` object at the top of [`scripts/library.js`](scripts/library.js) before starting a new adventure:

```js
globalThis.WorldCalendarSettings = {
  START_DATE: { year: 2000, month: 1, day: 1 },
  ERA: "AD",
  CALENDAR_CARD_TITLE: "World Calendar",
  MAX_SKIP_YEARS: 1000,
  AUTO_SKIP_LIMIT_DAYS: 7
};
```

In an adventure, edit the `Date:` line in the World Calendar Story Card to set the current date (for example, `Date: 2026-11-25`). Edit its Description to change `Enabled` or `Auto-Skip Limit`. The season is calculated automatically.

### Optional scripts

- **Inner Self:** open the `Configure Inner Self` Story Card and set `Enable Inner Self` to `true`.
- **Auto-Cards:** open the `Edit to enable Auto-Cards` Story Card and set `Enable Auto-Cards` to `true`.

## Credits and licenses

Simple Calendar is derived from World Calendar by wertyqazx (Jubami). Inner Self and Auto-Cards are by LewdLeah.

- [World Calendar license](LICENSE-World-Calendar.txt)
- [Inner Self and Auto-Cards license](LICENSE-Inner-Self-and-Auto-Cards.txt)

The bundled scripts are distributed under their respective MIT licenses.
