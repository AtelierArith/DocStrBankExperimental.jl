```
GoalCountHeuristic(dir=:forward)
```

Heuristic that counts the number of goals un/satisfied. Can be used in either the `:forward` or `:backward` direction. The latter should be used for search with [`BackwardPlanner`](@ref).
