```
Domain([T=Float64,] dimensions, lower_boundary, upper_boundary, [mapping])
```

Three-dimensional Cartesian domain of size `dimensions`, periodic along the first two coordinate directions and delimited by `lower_boundary` and `upper_boundary` along the third coordinate direction.

# Arguments

  * `T::DataType = Float64`: Type that is used for coordinates and fields inside domain.
  * `dimensions::Tuple`: Size of the domain. The third dimension can be specified as a single value, in which case the domain is assumed to start at $x_3=0$ or as a tuple with the minimum and maximum $x_3$ values. If it is omitted, the default of $x_3 ∈ [0,1]$ is assumed, unless a custom `mapping` is provided.
  * `lower_boundary`, `upper_boundary`: Boundary definitions.
  * `mapping`: A non-linear mapping from the interval $[0,1]$ to the range of $x_3$ values, instead of the default linear mapping. The mapping can either be specified as a tuple of two functions representing the mapping and its derivative, or using the predefined [`SinusoidalMapping`](@ref). In the former case, the third element of `dimensions` is ignored if specified; in the latter case the mapping is adjusted to the domain size.
