```julia
WeightedAStarPlanner(heuristic, h_mult; kwargs...)

```

Weighted A* search, which multiplies the heuristic estimate by `h_mult` when computing the $f$ value of a node. Nodes with the lowest $f$ value are expanded first.
