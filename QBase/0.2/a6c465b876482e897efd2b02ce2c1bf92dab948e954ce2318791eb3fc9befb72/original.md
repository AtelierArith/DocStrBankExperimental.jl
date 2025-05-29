```
generalized_bell_states( dim :: Int64 ) :: Vector{State{ComplexF64}
```

The generalized Bell basis density matrices. See  [`generalized_bell_kets`](@ref) for more details. A `DomainError` is thrown if `dim ≥ 2` is not satisfied.
