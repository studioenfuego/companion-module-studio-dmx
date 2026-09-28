# companion-module-studio-dmx

[Bitfocus Companion](https://bitfocus.io/companion) module for **[Studio DMX](https://github.com/studioenfuego/studio-dmx)** — an open-source, browser-based DMX lighting controller for real studio use. Control fixtures over Art-Net or USB from any device on your network.

## Features

- **Actions** — recall scenes, set/adjust fixture dimmers, set/adjust grand master, set/adjust group levels, blackout
- **Feedbacks** — fixture on/off, grand master level, group active
- **Variables** — live grand master %, per-fixture dimmer %, per-group level %
- **Knob support** — adjust actions with ±% step for Stream Deck+ encoders

## Requirements

- **[Studio DMX](https://github.com/studioenfuego/studio-dmx)** running on your local network — see its README for setup instructions
- Bitfocus Companion 5.x

## Connection Setup

After adding the connection in Companion, set:

| Field | Value |
|-------|-------|
| Host | IP of the machine running Studio DMX (or `localhost`) |
| Port | Studio DMX server port (default `3333`) |

## Actions

| Action | Options |
|--------|---------|
| Recall Scene | Scene (dropdown), Fade time (ms) |
| Set Fixture Dimmer | Fixture (dropdown), Level % |
| Adjust Fixture Dimmer (knob) | Fixture (dropdown), Step % (+/−) |
| Set Grand Master | Level % |
| Adjust Grand Master (knob) | Step % (+/−) |
| Set Group Level | Group (dropdown), Level % |
| Adjust Group Level (knob) | Group (dropdown), Step % (+/−) |
| Blackout | — |

## Feedbacks

| Feedback | Description |
|----------|-------------|
| Fixture is On | True when fixture dimmer ≥ threshold % |
| Grand Master at level | True when grand master ≥ threshold % |
| Group is Active | True when group level ≥ threshold % |

## Variables

Replace `StudioDMX` with your connection label.

| Variable | Description |
|----------|-------------|
| `$(StudioDMX:grand_master_percent)` | Grand master 0–100 |
| `$(StudioDMX:grand_master_value)` | Grand master raw 0–255 |
| `$(StudioDMX:fixture_<name>_dimmer_percent)` | Fixture dimmer % (name slugified) |
| `$(StudioDMX:group_<name>_level_percent)` | Group level % (name slugified) |

Slugification: `"Front Wash"` → `front_wash` (lowercase, non-alphanumeric → `_`)

## Stream Deck+ Knob Setup

1. Add a button in **Encoder** mode
2. Rotate CW → **Adjust Grand Master (knob)** → Step: `5`
3. Rotate CCW → same action → Step: `-5`
4. Button label: `GM $(StudioDMX:grand_master_percent)%`

## Building from source

```bash
npm install
npm run build   # type-check + bundle → main.js
```

## License

MIT
