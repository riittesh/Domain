# Free .in Subdomains — alphaxgen.in 🇮🇳

> Get a free `yourname.alphaxgen.in` address for your website. No cost, no credit card.

**Status: Prototype (demo mode).** The landing page and name checker work in the browser. The live backend (accounts, database, automatic DNS) is under development. No real subdomains are issued yet.

---

## What is this?

Free-domain Platform is an open-source project that lets anyone in India (and beyond) claim a free subdomain under **alphaxgen.in** and point it at their website, for example:

- `rahul.alphaxgen.in`
- `myshop.alphaxgen.in`
- `portfolio.alphaxgen.in`

These are real, working internet addresses ending in `.in`. The project owner registers one paid domain (`alphaxgen.in`) and shares names under it for free, the same model used by services such as Odoo, Wix and is-a.dev.

### Important clarification

This project does **not** create new, standalone `.in` registrations such as `rahul.in`. Those can only be registered through the official .IN Registry and its accredited registrars, and they carry a fee. This platform provides **subdomains** of a domain the project owns.

---

## Features

### Available in the prototype
- Name search with instant availability feedback
- Validation: 3–40 characters, letters, numbers and single hyphens, no hyphen at start or end
- Reserved-name list (`www`, `mail`, `admin`, `api`, and others)
- Blocked lookalike names (banks, government, payment apps) to reduce phishing
- Claim flow with email and target-website fields
- Preview of the DNS record that would be created
- Responsive layout with automatic light and dark mode

### Planned
- User accounts and email verification
- Server-side unique-name enforcement (database unique constraint)
- Automatic DNS record creation through the Cloudflare API
- Automatic HTTPS
- Dashboard to update or delete a subdomain
- Abuse report form and admin takedown tools
- Rate limiting and bot protection
- Hindi and other Indian-language interface

---

## How it works (target architecture)

```
User ──▶ Landing page (Cloudflare Pages)
            │
            ▼
        Backend API (Cloudflare Worker)
            │  validates name, checks limits, verifies email
            ▼
        Database (unique name → owner, target)
            │
            ▼
        Cloudflare DNS API ──▶ creates CNAME: name.alphaxgen.in → user's site
```

1. The user searches for a name.
2. The backend checks the name against rules and the database.
3. After email verification, the backend creates a CNAME record pointing to the user's hosting address (for example `mysite.pages.dev`).
4. The user's site becomes reachable at `name.alphaxgen.in` over HTTPS.

---

## Project structure

```
free-in-domain-platform/
├── index.html        # Landing page and name checker (prototype)
├── README.md         # This file
└── docs/
    ├── architecture.md   # Planned backend design
    └── domain-policy.md  # Naming rules and acceptable use
```

---

## Run it locally

No build step or dependencies are needed.

1. Download or clone the repository.
2. Open `index.html` in any modern browser.

To host it free, connect the repository to **Cloudflare Pages** or enable **GitHub Pages** in the repository settings.

---

## Naming rules

- 3 to 40 characters
- Lowercase letters `a–z`, numbers `0–9` and hyphens
- Cannot start or end with a hyphen, and cannot contain `--`
- Names are first come, first served
- Reserved names and names imitating banks, government bodies or payment services are not allowed

## Acceptable use

Sites using a subdomain must not host or promote phishing, malware, scams, illegal content, spam or impersonation. Violating sites will be removed without notice. Report abuse through the report form once it is live.

---

## Security principles

- DNS provider credentials stay on the server and are never exposed to users or browser code.
- Name allocation is enforced by a database unique constraint, not by browser checks.
- Every request is validated and rate-limited.
- Users can only modify records they own.

---

## Roadmap

| Phase | Goal | Status |
| --- | --- | --- |
| 1 | Landing page and name checker | ✅ Prototype done |
| 2 | Register alphaxgen.in and move DNS to Cloudflare | ⏳ Pending |
| 3 | Backend: accounts, database, DNS automation | 🔜 Planned |
| 4 | Abuse reporting, admin tools, rate limits | 🔜 Planned |
| 5 | Public launch | 🔜 Planned |
| 6 | Explore sponsorships for standalone `.in` names | 💡 Idea |

---

## Costs and sustainability

- Platform software, hosting and DNS run on free tiers (Cloudflare, GitHub). Free-tier limits can change.
- The only fixed cost is the yearly renewal of `alphaxgen.in`, which must be kept up or every subdomain stops working.

---

## Contributing

Contributions are welcome: bug reports, ideas, translations and code.

1. Fork the repository
2. Create a branch: `git checkout -b feature/your-feature`
3. Commit your changes and open a pull request

## License

Add a license of your choice (for example MIT) in a `LICENSE` file.

## Disclaimer

This project is independent and is not affiliated with the .IN Registry, NIXI or any registrar. Subdomains are provided as-is, with no guarantee of availability.

---

**Maintainer:** AlphaXGen · Website: https://alphaxgen.in (planned) · Current site: https://alphaxgen.store
