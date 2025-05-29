```julia
GreedyPlanner(heuristic; kwargs...)

```

Greedy best-first search, with cycle checking. Nodes with the lowest heuristic value are expanded first (i.e. the cost of reaching them from the initial state is ignored).
