---
name: persyst
description: >-
  Use your organization's tools through Persyst — code repositories, Asana,
  Notion, Google Drive, Search Console, databases and other MCP servers your
  teams and clients have access to. Use when the user asks about code, tasks,
  documents or data that live in those tools. Covers how to discover
  connectors, pick one when several match, write actions, and guides.
---

# Persyst

Persyst connects an organization's tools to your AI client. You only see what
the user's teams and clients give them access to; there is no project to name.

## Discover first

Call `list_connectors` before anything else when you don't already know what
is available. It lists each connector, where it comes from (a team, a client,
the organization, or the user's own account) and the tools it exposes.

When several connectors of the same family could answer, pass the family
identifier the tool asks for:

- `connector_label` for a database or Batch,
- `repo` for a code repository,
- `siteUrl` for a Search Console property.

If the request is ambiguous between two connectors, ask rather than guess.

## Reading

Prefer the search tools (repository search, Asana task search, document
search) over listing everything. Quote the source (repository, task, page) in
your answer so the user can check it.

Databases are read-only. Keep queries narrow: select the columns you need and
add a limit.

## Writing

Some actions (creating an Asana task, editing a Notion page) are done in the
user's own name. If the tool answers that a personal account is missing, give
the user the link it returns so they can connect their account, then retry.

Announce what you are about to write before doing it. Every call is logged and
visible to the organization's administrators.

## Guides

`load_skill` returns ready-made guides (spec writing, code review, database
querying…). Load one when the task matches its title instead of improvising
the method.
