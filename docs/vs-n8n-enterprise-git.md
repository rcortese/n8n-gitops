---
sidebar_position: 7
title: n8n-gitops vs n8n Enterprise Git
---

# n8n-gitops vs n8n Enterprise Git

This guide explains how the n8n-gitops CLI compares to the Git integration that ships with n8n Enterprise so you can pick the best fit for your team and runtime.

## Quick Comparison

| Area                | n8n-gitops                                                                                                                         | n8n Enterprise Git                                                                                                                              |
|---------------------|------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| Availability        | Open source CLI; works with Community Edition, cloud plans with API access (Start/Pro), and self-hosted Business/Enterprise        | Built-in Enterprise feature inside the n8n UI                                                                                                   |
| Control surface     | GitOps-first CLI; designed for local dev and CI/CD                                                                                 | UI-driven Git integration managed from within n8n                                                                                               |
| Sync model          | Mirror exports keep a repo identical to the instance; optional code externalization; manifest + credential documentation generated | Syncs native workflow JSON between the instance and a connected repo; workflows stay in inline JSON                                             |
| Deployment          | Deploy from any Git ref/working tree to a target instance with plan/backup/prune options and active-state control                  | Changes are applied from the n8n instance you are signed into; promotion across environments means connecting each instance to Git separately   |
| Validation          | CLI validation of manifests and include directives before deploy                                                                   | Relies on n8n’s built-in validation when saving/publishing in the UI                                                                            |
| Credential handling | Credentials never exported; generates a credential dependency doc for awareness                                                    | Credentials remain inside n8n; Git history contains workflow definitions only                                                                   |
| PRs / Rollback      | Standard Git PR/revert flow; deploy any ref (tag/branch/commit); rollback by deploying a prior ref                                 | PRs live in your repo but n8n does not auto-deploy from them; rollback means syncing a prior commit/tag back into each connected instance       |

## When n8n-gitops Fits Best

- Running Community Edition or self-hosted instances without Enterprise licensing.
- Automating exports, reviews, and deployments through Git-based pipelines.
- Keeping code in first-class files via include directives for better reviews and testing.
- Promoting the same Git revision across multiple environments from CI/CD.
- Enforcing clean, reproducible deployments (mirror mode, pruning, backups, validation).

## When n8n Enterprise Git Fits Best

- Teams already on n8n Enterprise who want Git history directly inside the product UI.
- Collaborators who prefer UI-driven push/pull without additional tooling.
- Single-instance scenarios where in-app versioning is sufficient and externalized code files are not required.

## Plan Compatibility (as Dec/2025)

| Plan                            | n8n-gitops (open source)   | n8n Enterprise Git Sync |
|---------------------------------|----------------------------|-------------------------|
| Community                       | ✅ Supported                | ❌ Not available         |
| Cloud Starter                   | ✅ Supported                | ❌ Not available         |
| Cloud Pro                       | ✅ Supported                | ❌ Not available         |
| Self-hosted Business/Enterprise | ✅ Supported                | ✅ Available             |

Notes:
- n8n-gitops is **free/open source** and requires API access on your n8n plan.
- Enterprise Git Sync is only available on self-hosted Business/Enterprise; cloud Starter/Pro do not include it.
