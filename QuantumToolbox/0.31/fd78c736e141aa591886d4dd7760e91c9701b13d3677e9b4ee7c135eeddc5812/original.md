```
rand_unitary(dimensions, distribution=Val(:haar))
```

Returns a random unitary [`QuantumObject`](@ref).

The `dimensions` can be either the following types:

  * `dimensions::Int`: Number of basis states in the Hilbert space.
  * `dimensions::Union{Dimensions,AbstractVector{Int},Tuple}`: list of dimensions representing the each number of basis in the subsystems.

The `distribution` specifies which of the method used to obtain the unitary matrix:

  * `:haar`: Haar random unitary matrix using the algorithm from reference 1
  * `:exp`: Uses $\exp(-i\hat{H})$, where $\hat{H}$ is a randomly generated Hermitian operator.

# References

1. [F. Mezzadri, How to generate random matrices from the classical compact groups, arXiv:math-ph/0609050 (2007)](https://arxiv.org/abs/math-ph/0609050)

!!! warning "Beware of type-stability!"
    If you want to keep type stability, it is recommended to use `rand_unitary(dimensions, Val(distribution))` instead of `rand_unitary(dimensions, distribution)`. Also, put `dimensions` as `Tuple` or `SVector` from [StaticArrays.jl](https://github.com/JuliaArrays/StaticArrays.jl). See [this link](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type) and the [related Section](@ref doc:Type-Stability) about type stability for more details.

