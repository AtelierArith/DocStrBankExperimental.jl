```
iscommuting(A::CircuitGate{L,G}, B::CircuitGate{M,H}) where {L,M,G,H}
```

は、一般の [`CircuitGate`](@ref) `A` と `B` が可換である場合に true を返します。
