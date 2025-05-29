```
JuMP.set_name(vref::DecisionVariableRef, name::String)::Nothing
```

Extend `JuMP.set_name` to set names of decision variables.

**Example**

```julia-repl
julia> set_name(vref, "var_name")

julia> name(vref)
"var_name"
```
