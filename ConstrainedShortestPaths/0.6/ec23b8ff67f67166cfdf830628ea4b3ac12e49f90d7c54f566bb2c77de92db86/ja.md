```julia
generalized_constrained_shortest_path_with_threshold(
    instance::ConstrainedShortestPaths.CSPInstance,
    threshold::Float64;
    kwargs...
) -> @NamedTuple{p_star::Vector{Vector{Int64}}, c_star::Vector{Float64}}

```

`instance`の最初と最後のノード間の最短経路を計算します。
