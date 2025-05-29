```julia
apply_kernel(
    kernel::Rocketeer.RocketKernel,
    x::AbstractVector{T} where T<:Real
) -> Any

```

# Summary

Apply a single [`RocketKernel`](@ref) to the sequence `x`.

# Arguments

  * `kernel::RocketKernel`: the [`RocketKernel`](@ref) used for computing features.
  * `x::RealVector`: data sequence for computing Rocket features.

# Method List / Definition Locations

```julia
apply_kernel(kernel, x)
```

defined at [`packages/Rocketeer/tbPiD/src/lib/rocket.jl:136`](file:///home/terasaki/.julia/packages/Rocketeer/tbPiD/src/lib/rocket.jl).
