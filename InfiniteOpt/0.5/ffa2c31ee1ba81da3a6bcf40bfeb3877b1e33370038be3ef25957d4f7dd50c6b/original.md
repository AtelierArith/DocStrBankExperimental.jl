```
JuMP.lower_bound(vref::UserDecisionVariableRef)::Float64
```

Extend `JuMP.lower_bound` to return the lower bound of an `InfiniteOpt` variable.  Errors if `vref` doesn't have a lower bound.

**Example**

```julia-repl
julia> lower_bound(vref)
0.0
```
