```
MultiAgentPolicy(agents::NT) where {NT<: NamedTuple}
```

MultiAgentPolicy is a policy struct that contains `<:AbstractPolicy` structs indexed by the player's symbol.
