```
planar_symmetric_qubit_povm( n :: Int64 ) :: POVM{Float64}
```

Constructs an `n`-element `POVM{Float64}` from the [`planar_symmetric_qubit_states`](@ref). Each state is multipled by a factor of `2/n` to satisfy the completeness relation.

A `DomainError` is thrown if `n ≥ 2` is not satisfied.
