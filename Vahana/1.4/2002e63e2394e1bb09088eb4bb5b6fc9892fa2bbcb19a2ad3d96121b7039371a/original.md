```
enable_asserts(enable::Bool)
```

Vahana comes with some internal consistency checks, at the cost of run-time performance (e.g., in [`agentstate`](@ref) there are checks that the specified agenttype matches the agent's ID, which creates of course some overhead). The assertions that could degrade the run performance can be disabled by calling `enable_asssertions(false)`.

The recommended approach is therefore to leave the assertions enabled during the development of the model, but to disable them when the model goes "into production", e.g. before the start of a parameter space exploration.
