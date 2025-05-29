```
JuMP.set_name(fref::ParameterFunctionRef, name::String)::Nothing
```

Extend `JuMP.set_name` to set the name of a parameter function.

**Example**

```julia-repl
julia> set_name(fref, "func_name")

julia> name(fref)
"func_name"
```
