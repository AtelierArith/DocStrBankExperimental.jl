```
MultiAgentHook(hooks::NT) where {NT<: NamedTuple}
```

MultiAgentHook is a hook struct that contains `<:AbstractHook` structs indexed by the player's symbol.
