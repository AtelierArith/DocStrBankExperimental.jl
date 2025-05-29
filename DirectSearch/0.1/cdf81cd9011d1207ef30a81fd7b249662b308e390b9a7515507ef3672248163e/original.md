```
SetVariableBounds(p::DSProblem{T}, l::Vector{T}, u::Vector{T}) where T
```

Call [`SetVariableBound`](@ref) for each variable. The vectors `l` and `u` should contain a lower and upper bound for each variable.
