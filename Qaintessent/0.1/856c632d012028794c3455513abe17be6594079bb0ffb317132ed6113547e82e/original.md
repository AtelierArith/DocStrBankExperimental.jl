```
iscommuting(A::CircuitGate{L,ControlledGate{G}}, B::CircuitGate{M,ControlledGate{G}}) where {L,M,G<:AbstractGate}
```

returns true if controlled [`CircuitGate`](@ref) `A` and `B` commute.
