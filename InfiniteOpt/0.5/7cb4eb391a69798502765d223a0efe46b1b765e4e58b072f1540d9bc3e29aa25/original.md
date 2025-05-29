```
JuMP.delete_upper_bound(vref::UserDecisionVariableRef)::Nothing
```

Extend `JuMP.delete_upper_bound` to delete the upper bound of `vref`. Errors if  it doesn't have an upper bound.

**Example**

```julia-repl
julia> delete_upper_bound(vref)

julia> has_upper_bound(vref)
false
```
