```
add_agent!(agent::AbstractAgent [, pos], model::ABM) → agent
```

Add the `agent` to the model in the given position. If `pos` is not given, the `agent` is added to a random position. The `agent`'s position is always updated to match `position`, and therefore for `add_agent!` the position of the `agent` is meaningless. Use [`add_agent_own_pos!`](@ref) to use the `agent`'s position. The type of `pos` must match the underlying space position type.
