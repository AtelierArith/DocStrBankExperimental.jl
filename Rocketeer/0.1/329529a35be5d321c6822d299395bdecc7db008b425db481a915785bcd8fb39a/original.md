```julia
apply_kernels(
    rocket::Rocketeer.RocketModule,
    x::AbstractVector{T} where T<:Real
) -> Matrix{Float64}

```

# Summary

Run a vector of [`RocketKernel`](@ref)s along a sequence `x`.

# Arguments

  * `rocket::RocketModule`: rocket module containing many kernels for processing.
  * `x::RealVector`: data sequence for computing rocket features.

# Method List / Definition Locations

```julia
apply_kernels(rocket, x)
```

defined at [`packages/Rocketeer/tbPiD/src/lib/rocket.jl:173`](file:///home/terasaki/.julia/packages/Rocketeer/tbPiD/src/lib/rocket.jl).
