```
SimpleInitiator(threshold = 1.0) <: InitiatorRule
```

Initiator rule to be passed to [`PDVec`](@ref) or [`InitiatorDVec`](@ref). An initiator is a configuration `add` with a coefficient with magnitude `abs(v[add]) > threshold`. The `threshold` can be passed as a keyword argument. Rules:

  * Initiators can spawn anywhere.
  * Non-initiators cannot spawn.

See [`InitiatorRule`](@ref).
