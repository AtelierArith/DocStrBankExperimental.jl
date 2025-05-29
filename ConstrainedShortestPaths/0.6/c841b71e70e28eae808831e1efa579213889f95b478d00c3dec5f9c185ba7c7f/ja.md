```julia
generalized_a_star_with_threshold(
    instance::ConstrainedShortestPaths.CSPInstance,
    bounds,
    threshold::Float64;
    kwargs...
) -> @NamedTuple{p_star::Vector{Vector{Int64}}, c_star::Vector{Float64}}

```

閾値未満のすべてのパスを計算します。
