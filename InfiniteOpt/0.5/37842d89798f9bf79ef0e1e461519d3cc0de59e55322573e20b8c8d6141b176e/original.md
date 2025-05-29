```
JuMP.unfix(vref::UserDecisionVariableRef)::Nothing
```

Extend `JuMP.unfix` to unfix `vref`. Errors if it is not fixed.

**Example**

```julia-repl
julia> unfix(vref)

julia> is_fixed(vref)
false
```
