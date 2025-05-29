```
singular(result; multiple_results=false, kwargs...)
```

Return all [`PathResult`]s for which the solution is singular. If `multiple_results=false` only one point from each cluster of multiple solutions is returned. If `multiple_results = true` all singular solutions in `R` are returned. For the possible `kwargs` see [`results`](@ref).
