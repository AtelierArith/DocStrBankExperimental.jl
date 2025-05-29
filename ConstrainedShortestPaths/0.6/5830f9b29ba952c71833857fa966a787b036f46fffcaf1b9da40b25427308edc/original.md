```julia
generalized_a_star(
    instance::ConstrainedShortestPaths.ForwardCSPInstance;
    kwargs...
) -> NamedTuple{(:p_star, :c_star, :info), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_dominance::Int64}}}

```

Label dominance dynamic programming without bounding.
