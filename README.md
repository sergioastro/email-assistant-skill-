# Email Assistant Skill

An AI skill with comprehensive email processing rules. Designed for an AI assistant that monitors multiple mailboxes and sends notifications to Telegram.

## What It Does

- Classifies incoming emails into 7 categories
- Performs automatic actions (archive, move, star)
- Sends Telegram notifications with summaries and inline buttons
- Generates draft replies
- Detects phishing and suspicious emails
- Extracts deadlines and due dates from emails
- Reminds about unanswered messages

## Email Categories

| Category | Action |
|---|---|
| **Important** | Inbox + star |
| **Finance** | Inbox + "Finance" label |
| **Invoice** | "Invoice" folder |
| **Service Notifications** | Inbox (weekly cleanup to archive) |
| **Marketing** | Archive |
| **Spam** | Delete |
| **Personal** | Inbox |

## Features

### Notifications
- Separate templates for regular, important, suspicious emails, and invoices
- Thread grouping — one notification instead of many
- Deduplication across mailboxes
- Daily digest with statistics

### Smart Processing
- Dual categorization (an email can have 2 categories)
- Reply necessity and urgency detection
- Deadline extraction with countdown
- Phishing detection (domains, links, attachments)
- Invoice identification with amount and payment details extraction
- Content analysis for false threads (off-topic Re: replies)

### Draft Replies
- Auto-generated in the language of the incoming email + translation to Russian
- Safety guard for sensitive situations (hides "Send as is" button)

### Escalation
- 3 reminders with increasing urgency (4h / 24h / 48h)
- Emergency reminders for approaching deadlines
- Inline buttons: Reply / Snooze / Dismiss

### Security
- Masking of sensitive data (passwords, tokens, card numbers)
- Suspicious attachment warnings
- Unknown sender warnings for invoices
- Unsubscribe protection (filters for transactional emails)

### Telegram Interaction
- Inline buttons on every notification
- Email search via text queries
- Classification error correction (button + text command)
- Auto-unsubscribe from frequent newsletters
- Learning from user corrections

## Edge Cases

Covered: empty subject lines, email floods (20+ emails/hour), forwarded emails, calendar invites, bounce/delivery failures, image-only emails, auto-replies (OOO), already-read emails, CC vs To, foreign languages, URGENT labels from unknown senders.

## Usage

The `SKILL.md` file contains the full set of rules. Connect it as a skill to your AI assistant (Claude, GPT, or other) that processes incoming email.

### Claude Code
```
/plugin install email-assistant-skill
```

### Claude.ai
Upload `SKILL.md` via the skills settings.
