```julia
BiGreedyPlanner(f_heuristic, b_heuristic; kwargs...)

```

Bidirectional greedy best-first search, where `f_heuristic` is the forward search heuristic and `b_heuristic``is the backward search heuristic. Options specified as`kwargs` are shared by both the backward and forward search.
