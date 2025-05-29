```
JuMP.set_upper_bound(vref::UserDecisionVariableRef, upper::Real)::Nothing
```

Extend `JuMP.set_upper_bound` to specify the upper bound of an `InfiniteOpt`  variable `vref`. Errors if `vref` is fixed.

**Example**

```julia-repl
julia> set_upper_bound(vref, 1)

julia> upper_bound(vref)
1.0
```
