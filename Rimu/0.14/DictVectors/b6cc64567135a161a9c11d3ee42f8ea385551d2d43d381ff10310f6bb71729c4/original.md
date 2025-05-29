```
CoherentInitiator(threshold = 1.0) <: InitiatorRule
```

Initiator rule to be passed to [`PDVec`](@ref) or [`InitiatorDVec`](@ref). An initiator is a configuration `add` with a coefficient with magnitude `abs(v[add]) > threshold`. The `threshold` can be passed as a keyword argument. Rules:

  * Initiators can spawn anywhere.
  * Non-initiators can spawn to initiators.
  * Multiple non-initiators can spawn to a single non-initiator if their contributions add up to a value greater than the initiator threshold.

See [`InitiatorRule`](@ref).
