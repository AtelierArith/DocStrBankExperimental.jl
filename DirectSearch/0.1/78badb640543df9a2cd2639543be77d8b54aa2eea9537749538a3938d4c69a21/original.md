```
SetVariableBound(p::DSProblem{T}, index::Int, l::T, u::T) where T
```

Set the expected bounds of the variable with index `i` to between lower (`l`) and upper (`u`) values. This **does not** create a constraint, and is only used for scaling when a variable varies with a significantly different scale to the others.
