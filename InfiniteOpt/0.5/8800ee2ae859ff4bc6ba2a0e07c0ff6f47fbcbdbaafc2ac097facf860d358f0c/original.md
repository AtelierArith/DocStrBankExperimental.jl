```
JuMP.unset_integer(vref::UserDecisionVariableRef)::Nothing
```

Extend `JuMP.unset_integer` to unset `vref` as an integer variable. Errors if it  is not an integer variable.

```julia-repl
julia> unset_integer(vref)

julia> is_integer(vref)
false
```
