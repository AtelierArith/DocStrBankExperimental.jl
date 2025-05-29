```julia
generalized_a_star(
    instance::ConstrainedShortestPaths.ForwardCSPInstance;
    kwargs...
) -> NamedTuple{(:p_star, :c_star, :info), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_dominance::Int64}}}

```

境界なしの支配動的計画法にラベル付け。
