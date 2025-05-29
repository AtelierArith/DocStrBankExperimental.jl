```
PrecomputedHeuristic(heuristic::Heuristic, args...)
```

Wraps an existing `heuristic` and ensures that it is precomputed, preventing repeated pre-computation on subsequent calls to [`precompute!`](@ref).
