```
rand_dm(dimensions; rank::Int=prod(dimensions))
```

Generate a random density matrix from Ginibre ensemble with given argument `dimensions` and `rank`, ensuring that it is positive semi-definite and trace equals to `1`.

The `dimensions` can be either the following types:

  * `dimensions::Int`: Number of basis states in the Hilbert space.
  * `dimensions::Union{Dimensions,AbstractVector{Int},Tuple}`: list of dimensions representing the each number of basis in the subsystems.

The default keyword argument `rank = prod(dimensions)` (full rank).

!!! warning "Beware of type-stability!"
    If you want to keep type stability, it is recommended to use `rand_dm(dimensions; rank=rank)` with `dimensions` as `Tuple` or `SVector` from [StaticArrays.jl](https://github.com/JuliaArrays/StaticArrays.jl) instead of `Vector`. See [this link](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type) and the [related Section](@ref doc:Type-Stability) about type stability for more details.


# References

  * [J. Ginibre, Statistical ensembles of complex, quaternion, and real matrices, Journal of Mathematical Physics 6.3 (1965): 440-449](https://doi.org/10.1063/1.1704292)
  * [K. Życzkowski, et al., Generating random density matrices, Journal of Mathematical Physics 52, 062201 (2011)](http://dx.doi.org/10.1063/1.3595693)
