```
thermal_dm(N::Int, n::Real; sparse::Union{Bool,Val}=Val(false))
```

Density matrix for a thermal state (generating thermal state probabilities) with the following arguments:

  * `N::Int`: Number of basis states in the Hilbert space
  * `n::Real`: Expectation value for number of particles in the thermal state.
  * `sparse::Union{Bool,Val}`: If `true`, return a sparse matrix representation.

!!! warning "Beware of type-stability!"
    If you want to keep type stability, it is recommended to use `thermal_dm(N, n, sparse=Val(sparse))` instead of `thermal_dm(N, n, sparse=sparse)`. See [this link](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type) and the [related Section](@ref doc:Type-Stability) about type stability for more details.

