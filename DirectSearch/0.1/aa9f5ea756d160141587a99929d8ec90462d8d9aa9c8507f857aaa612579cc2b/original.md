```
AddProgressiveConstraint(p::AbstractProblem, c::Vector{Function})::Vector{Int}
```

Register a group of functions that define progressive barrier constraints. Calls [`AddProgressiveConstraint`](@ref) on each function individually.
