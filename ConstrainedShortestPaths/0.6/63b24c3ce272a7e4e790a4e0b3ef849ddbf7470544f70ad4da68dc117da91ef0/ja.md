```julia
generalized_a_star(
    instance::ConstrainedShortestPaths.CSPInstance{T, G, FR},
    bounds;
    kwargs...
) -> NamedTuple{(:p_star, :c_star, :info, :bounds), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_bounds::Int64, nb_cuts_with_dominance::Int64}, Any}}

```

インスタンスに対して境界を使用して一般化されたA*アルゴリズムを実行します（[一般化された `A^\star`](@ref)を参照）。
