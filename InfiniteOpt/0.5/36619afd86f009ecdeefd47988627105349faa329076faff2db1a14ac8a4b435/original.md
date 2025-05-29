```
JuMP.name(vref::DecisionVariableRef)::String
```

Extend `JuMP.name` to return the names of `InfiniteOpt` variables.

**Example**

```julia-repl
julia> name(vref)
"var_name"
```
