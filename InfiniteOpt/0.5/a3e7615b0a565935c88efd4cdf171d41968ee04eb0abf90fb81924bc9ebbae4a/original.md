```
JuMP.delete(model::InfiniteModel, cref::InfOptConstraintRef)::Nothing
```

Extend `JuMP.delete` to delete an `InfiniteOpt` constraint and all associated  information. Errors if `cref` is invalid.

**Example**

```julia-repl
julia> print(model)
Min measure(g(t)*t) + z
Subject to
 z ≥ 0.0
 g(t) + z ≥ 42.0, ∀ t ∈ [0, 6]

julia> delete(model, cref)

julia> print(model)
Min measure(g(t)*t) + z
Subject to
 z ≥ 0.0
```
