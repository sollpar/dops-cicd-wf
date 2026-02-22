# Copilot Instructions for dops-cicd-wf

This repository is intentionally minimal: it exists to demonstrate a GitHub
Actions CI/CD workflow.  The only real artifact is the workflow YAML in
`.github/workflows/github-actions.yaml` and a one–line README.  When working in
this project an AI coding agent should keep the following points in mind.

---

## Big Picture

- **Purpose:** A playground for GitHub Actions.  There are no application
  sources, libraries, or services to build.  The focus is on editing
  the workflow and any ancillary documentation.
- **Workspace layout:**
  ```text
  /workspaces/dops-cicd-wf
  ├── README.md           # brief description
  └── .github/
      └── workflows/
          └── github-actions.yaml  # the demo workflow
  ```
- **No runtime code:** There are no `src/`, `pkg/`, or similar folders.  If a
  task asks you to "add a feature" you will almost always be modifying the
  workflow or the README, not writing new application logic.

## Workflow specifics

- The YAML defines a single job called `Explore-GitHub-Actions` that runs on
  `ubuntu-latest`.  It simply echoes environment variables and lists files.
- Workflow is triggered on every `push`.
- Common modifications:
  - add new jobs/steps for building, linting or testing if the repo later
    contains code.
  - adjust the `on:` triggers to include `pull_request` or manual `workflow_dispatch`.
  - use `actions/checkout@v5` to clone the repository (see existing step).
- When writing or editing YAML, maintain the indentation style shown in the
  existing file – two spaces per level and keys aligned.

## Developer workflows

- **Testing changes:** Push to any branch; the GitHub Actions workflow will
  run automatically.  There is no local build system in this repo.
- **Adding new files:** Simply commit them; there is no special generation
  step.  If new code is ever added, ensure the workflow covers it.
- **Debugging workflows:** Use `echo` statements and `ls` as shown.  GitHub
  runner is a standard Ubuntu container; you can run commands like
  `uname -a` or `df -h` if additional context is needed.

## Conventions and patterns

- YAML step names are written in sentence case with an emoji in the demo but
  emojis are not required.
- Branch names and job names should be descriptive; the sample uses
  `Explore-GitHub-Actions` to make the demo clear.
- The README is intentionally sparse; if the project grows, update the
  README with new instructions or architectural notes.

## Integration points and dependencies

- **External actions:** currently only `actions/checkout@v5`.  Any future
  jobs should pin versions similarly and run from the official GitHub
  marketplace.
- **No other integrations:** There are no Dockerfiles, cloud provider
  configurations, or third‑party libraries.

---

> 🚧 **Note for the AI agent:** This project is intentionally simplistic. If a
> user asks you to add features that seem unrelated to CI/CD, double-check
> whether they mean to extend this repository or if they accidentally opened
> a different project.  When in doubt, ask for clarification.

Please review and let me know if any section feels unclear or incomplete.