```julia
AStarPlanner(heuristic; kwargs...)

```

A* search. Nodes with the lowest $f$ value are expanded first. This is guaranteed to produce a cost-optimal solution if the `heuristic` is admissible.
