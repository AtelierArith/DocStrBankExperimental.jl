```
agentstate_flexible(sim, id::AgentID)
```

Returns the state of an agent with the `id`, where the type of the agent is determined at runtime. If the type is known at compile time, using [`agentstate`](@ref) is preferable as this improves performance.
