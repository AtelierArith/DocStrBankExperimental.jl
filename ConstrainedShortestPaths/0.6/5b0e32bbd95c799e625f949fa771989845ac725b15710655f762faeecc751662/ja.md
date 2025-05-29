```julia
compute_bounds(
    instance::ConstrainedShortestPaths.CSPInstance{T, G, FR, BR};
    kwargs...
) -> Dict{Int64}

```

インスタンスの逆境界を計算します（[Computing bounds](@ref)を参照）。
