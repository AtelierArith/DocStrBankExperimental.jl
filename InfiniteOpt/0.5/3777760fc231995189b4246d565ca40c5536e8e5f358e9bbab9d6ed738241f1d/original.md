```
JuMP.set_lower_bound(vref::UserDecisionVariableRef, lower::Real)::Nothing
```

Extend `JuMP.set_lower_bound` to specify the lower bound of an `InfiniteOpt`  variable `vref`. Errors if `vref` is fixed.

**Example**

```julia-repl
julia> set_lower_bound(vref, -1)

julia> lower_bound(vref)
-1.0
```
