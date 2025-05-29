```
register(
container,
agent,
suggested_aid::Union{String,Nothing}=nothing;
kwargs...,
```

)

Register the agent to the container. Retun the agent itself for convenience.

Normally the aid is generated, however it is possible to suggest an aid, which will be used if it has not been used yet and if it is not conflicting with the default naming pattern (agent0, agent1, ...)
