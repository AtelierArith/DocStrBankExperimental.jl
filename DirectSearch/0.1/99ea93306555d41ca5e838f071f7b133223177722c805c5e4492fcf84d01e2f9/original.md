```
AddExtremeConstraint(p::AbstractProblem, c::Vector{Function}; index::CollectionIndex=CollectionIndex(1))
```

Register a group of functions that define extreme barrier constraints. Calls [`AddExtremeConstraint`](@ref) on each function individually.
