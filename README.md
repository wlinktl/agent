# agent-lab

One-day Python lab for a Java developer moving into AI agent development.

```powershell
uv sync                      # create .venv and install dependencies
uv run pytest                # run every exercise's tests
uv run ruff check .          # lint
uv run ruff format .         # format

# Run individual exercises
uv run python -m agent_lab.b1_basics
uv run python -m agent_lab.b5_async

# Agent (needs ANTHROPIC_API_KEY in your environment)
$env:ANTHROPIC_API_KEY = "<your key>"
uv run python -m agent_lab.agent "What is 17% of 2340, and how warm is Paris in fahrenheit?"


uv run python -m agent_lab.agent --mode stream "Explain Python generators to a Java developer"
```

## Migration agent

`agent_lab.migrate` upgrades the sample app in `migration/` from Java 17, Spring Boot 2.7 and
Angular 18 to Java 21, Spring Boot 4.0 and React 19. See
[docs/migration/comparison.md](docs/migration/comparison.md).

```powershell
$env:MIGRATE_JAVA_HOME = "C:\devtool\jdk21"
uv run python -m agent_lab.migrate migration\runs\python-agent --no-llm       # no API key, no cost
uv run python -m agent_lab.migrate migration\runs\python-agent --budget-usd 5 # full run
```

`agent_lab.migrate.compare` runs the same user flows in the old and the new app and reports
what differs. See [docs/migration/comparison-testing.md](docs/migration/comparison-testing.md).

The model defaults to `claude-opus-5`. Override it with the `AGENT_LAB_MODEL` environment variable.
"# agent" 
