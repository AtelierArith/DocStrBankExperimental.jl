```
JuMP.get_optimizer_attribute(model::InfiniteModel,
                             attr::MOI.AbstractOptimizerAttribute)
```

Extend `get_optimizer_attribute` to return the value of the solver-specific  attribute `attr` in `model`.

**Example** `julia-repl julia> get_optimizer_attribute(model, MOI.Silent()) true``
