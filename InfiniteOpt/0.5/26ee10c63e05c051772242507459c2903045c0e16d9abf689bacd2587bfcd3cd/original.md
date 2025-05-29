```
JuMP.delete(model::InfiniteModel, vref::DecisionVariableRef)::Nothing
```

Extend `JuMP.delete` to delete `InfiniteOpt` variables and their dependencies.  Errors if variable is invalid, meaning it has already been deleted or it belongs  to another model.

**Example**

```julia-repl
julia> print(model)
Min measure(g(t)*t) + z
Subject to
 z ≥ 0.0
 g(t) + z ≥ 42.0, ∀ t ∈ [0, 6]
 g(0.5) = 0

julia> delete(model, g)

julia> print(model)
Min measure(t) + z
Subject to
 z ≥ 0.0
 z ≥ 42.0
```
