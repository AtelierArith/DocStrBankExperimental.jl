```
nonsingular(result; conditions...)
```

Return all [`PathResult`](@ref)s for which the solution is non-singular. This is just a shorthand for `results(R; only_nonsingular=true, conditions...)`. For the possible `conditions` see [`results`](@ref).
