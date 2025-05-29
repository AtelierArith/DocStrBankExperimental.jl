```
JuMP.delete_lower_bound(vref::UserDecisionVariableRef)::Nothing
```

Extend `JuMP.delete_lower_bound` to delete lower bound of `vref`. Errors if it  doesn't have a lower bound.

**Example**

```julia-repl
julia> delete_lower_bound(vref)

julia> has_lower_bound(vref)
false
```
