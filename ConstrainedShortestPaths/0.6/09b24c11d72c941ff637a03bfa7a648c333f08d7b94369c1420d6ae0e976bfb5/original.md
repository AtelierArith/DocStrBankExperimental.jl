```julia
generalized_constrained_shortest_path(
    instance::ConstrainedShortestPaths.CSPInstance;
    kwargs...
) -> NamedTuple{(:p_star, :c_star, :info, :bounds), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_bounds::Int64, nb_cuts_with_dominance::Int64}, Dict{Int64}}}

```

Compute the shortest path of `instance`.
