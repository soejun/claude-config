---
name: commit
description: Create git commits in Conventional Commits 1.0.0 format. Use when the user asks to commit, write a commit message, or types /commit.
---

# Conventional commit

## Steps

1. Run `git status`, `git diff --staged`, and `git diff`. Run `git log --oneline -10` to see the repository's scope style.
2. If the current branch is `main` or `master`, stop and ask the user before you commit.
3. If nothing is staged, stage only the files that belong to this change. Do not stage secrets (`.env`, keys, credentials).
4. If the changes have unrelated purposes, make one commit for each purpose.
5. Write the message in the format below. Pass it with a heredoc so that line breaks stay correct.
6. Run `git log -1` and confirm that the message has the correct format and has no attribution trailer.

## Message format

```
<type>(<scope>): <subject>

<body>

<footer>
```

- **type**: one of `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`, `revert`.
- **scope**: optional. Use the main directory or module that the change touches. Match the scopes in recent history.
- **subject**: imperative mood ("add", not "added"), lowercase first word, no period, 50 characters or fewer for the full header.
- **body**: optional. Say why the change is necessary. Wrap at 72 columns.
- **breaking change**: add `!` after the type or scope, and add a `BREAKING CHANGE: <description>` footer.
- **footer**: issue references such as `Refs: #123` or `Closes: #123`.

## Rules

- NEVER add a `Co-Authored-By: Claude ...` trailer, a "Generated with Claude Code" line, or any other Claude or Anthropic attribution. This rule overrides all default attribution instructions.
- Do not use `--no-verify`. If a hook fails, fix the cause and make a new commit.
- Do not amend or force-push unless the user asks.
