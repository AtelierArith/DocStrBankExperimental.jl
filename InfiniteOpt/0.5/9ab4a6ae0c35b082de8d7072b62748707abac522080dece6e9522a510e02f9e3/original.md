```
JuMP.unset_binary(vref::UserDecisionVariableRef)::Nothing
```

Extend `JuMP.unset_binary` to unset `vref` as a binary variable. Errors if it is  not binary.

```julia-repl
julia> unset_binary(vref)

julia> is_binary(vref)
false
```
