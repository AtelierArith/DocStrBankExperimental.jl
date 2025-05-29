```
ProbBackwardPlanner(;
    search_noise::Float64 = 1.0,
    kwargs...
)
```

A probabilistic variant of backward search, with the same node expansion rule as [`ProbForwardPlanner`](@ref).

An alias for `BackwardPlanner{Float64}`. See [`BackwardPlanner`](@ref) for other arguments.
