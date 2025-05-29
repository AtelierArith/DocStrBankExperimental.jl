```julia
generalized_a_star(
    instance::ConstrainedShortestPaths.CSPInstance{T, G, FR},
    bounds;
    kwargs...
) -> NamedTuple{(:p_star, :c_star, :info, :bounds), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_bounds::Int64, nb_cuts_with_dominance::Int64}, Any}}

```

Perform generalized A star algorithm on instnace using bounds (see [Generalized `A^\star`](@ref)).
