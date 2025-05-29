```
Session(agent::Agent;
    context::Dict{Symbol, Any} = Dict{Symbol, Any}())
```

Initializes a `Session` with an `agent` and an optional `context`.

Run `run_full_turn!` with a `user_prompt` to continue the session.
