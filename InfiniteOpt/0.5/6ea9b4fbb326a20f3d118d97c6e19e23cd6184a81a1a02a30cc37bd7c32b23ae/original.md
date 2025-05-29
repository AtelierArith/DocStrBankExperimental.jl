```
JuMP.upper_bound(vref::UserDecisionVariableRef)::Float64
```

Extend `JuMP.upper_bound` to return the upper bound of an `InfiniteOpt` variable.  Errors if `vref` doesn't have a upper bound.

**Example**

```julia-repl
julia> upper_bound(vref)
0.0
```
