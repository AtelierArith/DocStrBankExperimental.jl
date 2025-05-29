```
JuMP.set_name(cref::InfOptConstraintRef, name::String)::Nothing
```

Extend `JuMP.set_name` to specify the name of a constraint `cref`.

**Example**

```julia-repl
julia> set_name(cref, "new_name")

julia> name(cref)
"new_name"
```
