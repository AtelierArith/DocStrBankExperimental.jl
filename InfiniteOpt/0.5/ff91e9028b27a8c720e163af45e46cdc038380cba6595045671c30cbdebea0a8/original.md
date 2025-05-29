```
JuMP.get_optimizer_attribute(model::InfiniteModel, name::String)
```

Extend `get_optimizer_attribute` to return the value associated with the  solver-specific attribute named `name`.

**Example** `julia-repl julia> get_optimizer_attribute(model, "tol") 0.0001``
