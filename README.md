# techstax-action-repo
This is a GitHub Repository to demonstrate integration of GitHub Actions to record events as a logging system by sending the corresponding information in the form of payload to a webhook.

## 🚀 Features

- Sends webhook data on:
  - `PUSH` events
  - `PULL_REQUEST` opened events
  - `MERGE` (via `pull_request_target` closed event)
- Automatically triggers on GitHub events
- Sends structured JSON payloads to a Flask-based webhook receiver
- Uses GitHub Secrets to manage the webhook endpoint URL securely

## 💼 Payload Schema
```
{
  "_id": "<MongoDB ObjectId>"
  "request_id": "PR-14 / <commit-sha>",
  "author": "riyazuddin-1",
  "action": "PUSH | PULL_REQUEST | MERGE",
  "from_branch": "feature-branch",
  "to_branch": "main",
  "timestamp": "2025-07-11T17:30:00Z"
}
```

## 🧪 Testing the Workflow

1. Create a new branch and push changes
2. Open a Pull Request
3. Merge the PR into the base branch
4. Your webhook receiver should log three events:
   - One for the push
   - One for the pull_request opened
   - One for the merge (if merged)

## 🗃️ Related Repository

[techstax-webhook-repo](https://github.com/riyazuddin-1/techstax-webhook-repo): Flask app that receives the webhook data and stores it in MongoDB.

**NOTE**: These repositories are part of an assignment submission and are open for educational use.
