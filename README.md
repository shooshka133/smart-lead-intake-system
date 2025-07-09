# 🧠 Smart Lead Intake System

A fully automated, real-world-ready **lead intake pipeline** powered by **Google Forms**, **Google Sheets**, **n8n**, **Airtable**, **HubSpot**, **Slack**, and **Gmail**.

---

## 📌 Overview
This project captures lead submissions from a Google Form and automatically:
- Checks for duplicates
- Appends to either `Valid Leads` or `Duplicate Leads` sheet
- Enriches the lead with metadata (timestamps, source)
- Syncs to:
  - 📥 **Google Sheets** for team access
  - 📊 **Airtable CRM** for collaboration
  - 💼 **HubSpot CRM** for sales tracking
  - 🔔 **Slack** for instant lead alerts
  - 📧 **Gmail** for confirmation messages

It’s a **real-world lead capture system**, built to demonstrate automation, conditional logic, and API integrations.

---

## 🛠️ Tech Stack
| Tool | Purpose |
|------|---------|
| Google Forms | Lead collection form |
| Google Sheets | Form responses + Valid/Duplicate records |
| n8n | Automation engine (self-hosted) |
| Airtable | CRM-style table with lead filtering |
| HubSpot | Central CRM platform for tracking contacts |
| Slack | Internal lead notifications |
| Gmail | Auto-respond to sender |

---

## 🔄 Workflow Highlights

### 🧩 n8n Flow Summary
1. **Trigger:** Google Sheets Trigger (new row in "Form Responses 1")
2. **Extract Row:** Capture and label it with `source = Google Form`
3. **Check for Duplicates:** Compare email/name with `Valid Leads`
4. **Append:**
   - If duplicate → append to `Duplicate Leads`
   - Else → append to `Valid Leads`
5. **Enrich Metadata:** Format `Timestamp`, `slackTimeFormatted`, `Status = New`
6. **Sync Data:**
   - → Airtable (via upsert)
   - → HubSpot (via app token)
   - → Slack (message to `#new-leads` channel)
   - → Gmail (notification email to internal recipient)

### 🧠 Duplicate Logic
- Compares: `First Name`, `Last Name`, `Email`
- Uses `.toLowerCase()` for case-insensitive match

---

## 🧪 Sample Data Flow

![Workflow](workflow_n8n.png)

| Step | Screenshot |
|------|------------|
| Google Form | ![Form](Form.png) |
| Responses | ![Responses](Responses_1.png) |
| Valid Leads Sheet | ![Valid](Valid_lead.png) |
| Duplicate Leads Sheet | ![Duplicate](Duplicate_lead.png) |
| Airtable View | ![Airtable](Airtable_1.png) ![Airtable2](Airtable_2.png) |
| HubSpot Contact | ![HubSpot1](Hubspot_1.png) ![Hubspot2](Hubspot_2.png) |
| Slack Notification | ![Slack](Slack.png) |
| Gmail Confirmation | ![Gmail](Gmail.png) |

---

## ⚙️ Custom Fields

### Common Mappings
| Field | Description |
|-------|-------------|
| `Budget` | Numeric dropdown from form |
| `Urgency` | How soon the lead needs action |
| `Referral` | Lead referral source |
| `Project Type` | Type of service requested |
| `Company Name` | Custom string field |
| `Source` | Hardcoded as `Google Form` (set in Extract Node) |

---

## 🕓 Timestamps
All timestamps are:
- Initially stored in Google Sheet as **Excel serial numbers**
- Converted to:
  - ISO UTC format for HubSpot & Airtable
  - Formatted readable time (`Asia/Kuala_Lumpur`) for Slack

✅ This solves major timezone mismatch issues.

---

## 📥 Setup Instructions (Optional)
*Coming soon as a separate repo or Notion guide — let me know if you want this public.*

---

## 🎬 Upwork Demo Video
**Link/Embed** (optional placeholder):
`[Coming soon: walk-through video of live workflow]`

---

## 📎 License
MIT — for portfolio/demo purposes. Commercial use requires adaptation.

---

## 💡 Author
Ashraf Abd Elhalim — [Upwork Profile](#) | [GitHub](#)
