# ThreatAPI

A self-contained Windows API intelligence platform for malware analysts and threat researchers. Maps Windows API functions to attack techniques, detects malicious import patterns, and generates detection rules. All in a single HTML file with no dependencies.

Live at: https://sanskar-sudo.github.io/ThreatAPI/

---
<img width="1881" height="916" alt="image" src="https://github.com/user-attachments/assets/9d7739a0-5364-433f-8413-3beb88c5bde3" />


## What it does

**API Database**
240+ Windows API functions with risk scores, DLL origins, attack categories, and MITRE ATT&CK technique mappings. Fully searchable and filterable. Click any function to see which attack chains it appears in.

**Attack Chain Visualizer**
18 documented malware execution sequences including process hollowing, Early Bird APC injection, LSASS dumping, ransomware encryption, and DNS tunneling. Each chain shows a per-step API breakdown.

**PE Import Analyzer**
Paste a raw import table from any PE analysis tool and get instant results: matched APIs, identified attack patterns, MITRE technique IDs, and an overall severity rating.

**Risk Heatmap**
Visual overview of all APIs grouped by attack category or DLL, color-coded by severity score. Click any cell to drill into the full API detail.

**Export**
Generate YARA rules, Sigma rules, JSON, CSV, or raw IOC lists from any selection of APIs.

---

## Usage

No installation required. Open `threatapi.html` in any modern browser.

```bash
git clone https://github.com/your-username/threatapi
open threatapi/threatapi.html
```

To deploy, drop the file into any static host. GitHub Pages, Netlify, Cloudflare Pages, and Vercel all work with zero configuration.

---

## Stack

Pure HTML, CSS, and vanilla JavaScript. No frameworks, no build step, no external dependencies at runtime. The only network request is the Google Fonts import for IBM Plex Mono and IBM Plex Sans.

---

## Adding data

All API data is embedded directly in the file. To add or modify entries, edit the `DB.apis` array in the script block. Each entry follows this shape:

```js
{
  name:  'VirtualAlloc',
  dll:   'Kernel32.dll',
  cats:  ['Injection'],
  mitre: ['T1055'],
  risk:  'Critical',   // Critical | High | Medium | Low
  rv:    95,           // 0 to 100 risk score
  desc:  'Allocates memory in the process address space...'
}
```

---

## Inspired by

[MalAPI.io](https://malapi.io) by [@mrd0x](https://twitter.com/mrd0x)
