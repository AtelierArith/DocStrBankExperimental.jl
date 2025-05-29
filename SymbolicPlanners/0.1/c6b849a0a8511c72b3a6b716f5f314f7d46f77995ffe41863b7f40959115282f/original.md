```
PruningHeuristic(heuristic::Heuristic, pruner)
```

Combines an existing `heuristic` with `pruner`, an action pruning method that  defines the [`filter_available`](@ref) and [`filter_relevant`](@ref) functions. For example, `pruner` may be another heuristic that filters actions.
