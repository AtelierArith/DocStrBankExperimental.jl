```
rand_ket(dimensions)
```

Generate a random normalized [`Ket`](@ref) vector with given argument `dimensions`.

The `dimensions` can be either the following types:

  * `dimensions::Int`: Number of basis states in the Hilbert space.
  * `dimensions::Union{Dimensions,AbstractVector{Int},Tuple}`: list of dimensions representing the each number of basis in the subsystems.

!!! warning "Beware of type-stability!"
    If you want to keep type stability, it is recommended to use `rand_ket(dimensions)` with `dimensions` as `Tuple` or `SVector` from [StaticArrays.jl](https://github.com/JuliaArrays/StaticArrays.jl) to keep type stability. See the [related Section](@ref doc:Type-Stability) about type stability for more details.

