```
JuMP.is_valid(model::InfiniteModel, cref::InfOptConstraintRef)::Bool
```

Extend `JuMP.is_valid` to return `Bool` whether an `InfiniteOpt` constraint  reference is valid.

**Example**

```julia-repl
julia> is_valid(model, cref)
true
```
