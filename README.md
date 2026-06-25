# QuantLabs Harness Manager

Desktop app for macOS to run a QuantLabs-style LLM harness from a local folder.

## What it does

- Stores provider settings for local OpenAI-compatible servers, OpenAI, Anthropic, and DeepSeek.
- Tests an LLM connection from the UI.
- Runs a configurable harness command in a selected repository folder.
- Injects provider/model values into the command template.
- Captures stdout/stderr and reads JSON/JSONL result files.
- Persists app config under `~/Library/Application Support/QuantLabsHarness`.

## Run from source

```sh
python3 src/quantlabs_harness.py
```

## macOS app bundle

A ready-to-open app bundle is included at:

```text
outputs/QuantLabsHarness.app
```

If macOS blocks it because it is unsigned, open it with right click > Open.

## Command template variables

The harness command can use:

- `{provider}`
- `{provider_label}`
- `{base_url}`
- `{model}`
- `{api_key}`

Example:

```sh
python3 -m quantlabs.harness --provider {provider} --base-url {base_url} --model {model}
```

## Local LLM defaults

The local provider defaults to an OpenAI-compatible endpoint at:

```text
http://127.0.0.1:11434/v1
```

That works with Ollama when OpenAI-compatible serving is available. For LM Studio, point the Base URL to its local server, usually `http://127.0.0.1:1234/v1`.
