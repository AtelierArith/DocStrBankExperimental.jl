```
JuMP.name(cref::InfOptConstraintRef)::String
```

Extend `JuMP.name` to return the name of an `InfiniteOpt` constraint.

**Example**

```julia-repl
julia> name(cref)
"constr_name"
```
