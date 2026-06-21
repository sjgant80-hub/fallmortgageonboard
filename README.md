# ◊ FallMortgageOnboard

**Sovereign MCOB-shaped client onboarding for UK FCA-regulated mortgage brokers.** Single HTML file. Client data never leaves the device. Prime 863.

Part of the **mortgage-firm bundle**: [fallmortgage](https://github.com/sjgant80-hub/fallmortgage) (859) · **fallmortgageonboard** (863) · [fallmortgagepaper](https://github.com/sjgant80-hub/fallmortgagepaper) (877) · [fallmortgagepractice](https://github.com/sjgant80-hub/fallmortgagepractice) (881).

Live: <https://sjgant80-hub.github.io/fallmortgageonboard/>

---

## For the end user · the 30-second pitch

You're a mortgage broker onboarding a new client. You need a fact-find, AML CDD, source-of-deposit evidence, vulnerable customer assessment, and a lender submission pack — all before you can source. FallMortgageOnboard is one HTML file that walks you through the 11-step process, hashes every document, chains every action to an immutable audit trail, and keeps everything on your device.

### 11-step fact-find wizard

| Step | What it captures |
|---|---|
| 1. Type | Sole or joint application |
| 2. Applicant 1 | Name, DOB, nationality, NI, marital status |
| 3. Applicant 2 | Joint applicant details (skipped for sole) |
| 4. Contact & Property | Address, phone, email, subject property details |
| 5. Employment | Employment type, salary, other income (both applicants if joint) |
| 6. Expenditure | Monthly commitments, dependants — feeds affordability |
| 7. Credit | Adverse credit disclosure (CCJs, defaults, IVA, bankruptcy) |
| 8. Demands & Needs | MCOB 4.7A — mortgage type, loan amount, term, repayment, priorities |
| 9. AML CDD | MLR 2017 — ID/address verification, source of deposit, sanctions, PEP |
| 10. Vulnerable | FCA FG21/1 — category, adjustments, communication preferences |
| 11. Documents | Upload with SHA-256 hashing, expiry tracking, lender package checklist |

### How it works

1. Open the URL — demo data (James & Sarah Patterson, joint purchase) loads on first visit
2. **Firm** tab — set your firm name, FCA ref, network, PI insurer
3. **+ Adviser** — add yourself with CeMAP qualification and FCA ref
4. **+ Client** — 11-step wizard guides you through the full fact-find
5. **Client detail** — overview, employment, expenditure, demands, AML, vulnerability, documents
6. **Q & A** — ask regulatory questions (T0 offline rules + T3 BYOK)

### AML risk scoring

Automatic risk grading based on: PEP status, sanctions match, high-risk nationality, source of deposit, gift without letter, deposit amount. Three grades: low / medium / high. Enhanced due diligence flags surface on the dashboard.

### Audit chain (P3)

Every action appends a SHA-256 chained entry. Verify chain integrity from the Audit modal. Export separately for compliance records.

### Cross-tool mesh

BroadcastChannel `fall-mortgage` + `fall-client` + `fall-signal`. Syncs clients, advisers, and firm data from sibling tools.

---

## For the developer · architecture

- **Single HTML** · ~55KB · zero runtime dependencies
- **IndexedDB** (`fallmortgageonboard-v1`) · stores: firms, advisers, clients, documents, audit, state
- **BroadcastChannel** · `fall-mortgage` + `fall-client` + `fall-signal`
- **11-step wizard** · sole/joint branching · step-level collect/render
- **AML risk engine** · weighted scoring: PEP (3), sanctions (4), high-risk nationality (3), gift without letter (2), overseas deposit (2), large deposit (1)
- **T0** · 10 hard-coded MCOB/MLR/FG21 rules · zero network
- **T3** · BYOK Anthropic · falls back if T0 misses

### 14-pt sovereign gate

Single HTML · <400KB · Sovereign · IDB primary · KONOMI shim · fall-signal mesh · PWA manifest · Mobile responsive · T0 offline · Two-audience README · MIT · .nojekyll · Demo data · Audit chain

---

## Licence

MIT · Simon Gant · part of the [sjgant80-hub](https://github.com/sjgant80-hub) sovereign estate · prime 863 · ◊·κ=1.
