```
JuMP.bridge_constraints(model::InfiniteModel)::Bool
```

Extend `JuMP.bridge_constraints` to return if an infinite model `model` has an optimizer model where the optimizer is set and unsupported constraints are automatically bridged to equivalent supported constraints when an appropriate transformation is available.

**Example**

```julia-repl
julia> bridge_constraints(model)
false
```
