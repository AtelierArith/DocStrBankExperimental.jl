```
iscommuting(A::CircuitGate{L,ControlledGate{G}}, B::CircuitGate{M,ControlledGate{G}}) where {L,M,G<:AbstractGate}
```

は、制御された [`CircuitGate`](@ref) `A` と `B` が可換である場合に true を返します。
