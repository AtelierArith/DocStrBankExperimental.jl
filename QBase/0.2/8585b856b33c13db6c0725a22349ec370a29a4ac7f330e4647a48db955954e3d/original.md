```
mirror_symmetric_qubit_3povm( θ :: Real ) :: POVM{Float64}
```

Constructs a `POVM` aligned with the three mirror symmetric qubit states. The first measurement is aligned with the $|0\rangle$ state and the remaining two are symmetric across the z-axis.

A `DomainError` is thrown if argument `θ` ∉ [π/4,π/2].
