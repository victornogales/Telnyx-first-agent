# first-agent

A Telnyx agent, defined in configuration.

- `agent.json` — the agent: model, phone numbers, channels, tools, memory, limits, approvals. Edit it with `telnyx-acp add` / `remove`, or by hand, then `telnyx-acp validate`.
- `instructions.md` — what the agent is told. Plain Markdown; edit it and deploy again.
- `evals/basic.jsonl` — test conversations, one per line: `{"name", "input", "expect": {"contains", "regex", "judge", …}}`. `telnyx-acp eval` runs them.

```sh
telnyx-acp dev        # run it on this machine; text it from a second terminal
telnyx-acp deploy     # ship; the channels' webhooks now point at it
telnyx-acp invoke first-agent --conversation <id> "hello"
telnyx-acp eval       # score the replies to evals/ (--local against dev, --ci in a pipeline)
telnyx-acp logs --tail
```

`telnyx-acp deploy` writes `.telnyx/` beside these files and never commits it.
