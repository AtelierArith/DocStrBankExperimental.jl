```julia
compute_bounds(
    instance::ConstrainedShortestPaths.CSPInstance{T, G, FR, BR};
    kwargs...
) -> Dict{Int64}

```

Compute backward bounds of instance (see [Computing bounds](@ref)).
