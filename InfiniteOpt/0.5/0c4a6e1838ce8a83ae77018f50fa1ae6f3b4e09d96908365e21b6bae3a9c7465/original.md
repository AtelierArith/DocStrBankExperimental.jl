```
JuMP.set_start_value(vref::UserDecisionVariableRef, value::Real)::Nothing
```

Extend `JuMP.set_start_value` to specify the start value of `InfiniteOpt`  variables.

**Example**

```julia-repl
julia> set_start_value(vref, 1)

julia> start_value(vref)
1.0
```
