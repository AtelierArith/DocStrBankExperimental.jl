```
agentstate(sim, id::AgentID, ::Type{T})
```

Returns the state of an agent of type T.

In the case where the type T is not determinable when writing the code (e.g. since there may be edges between agents of different types, the function [`edges`](@ref) may also return agentIDs of different agent types), [`agentstate_flexible`](@ref) must be used instead.

!!! warning
    if agentstate is called with a Type{T} that does not match the type of the agent with `id` and the vahana assertions are disabled via [`enable_asserts`](@ref), then it is possible that the state of an incorrect agent will be returned. When the assertions are active, there is a runtime check that the agent with the ID `id` has indeed the type T.

