```
JuMP.set_optimizer_attribute(model::InfiniteModel,
                             attr::MOI.AbstractOptimizerAttribute,
                             value)
```

Extend `set_optimizer_attribute` to set the solver-specific attribute `attr` in  `model` to `value`.

**Example**

```julia-repl
julia> set_optimizer_attribute(model, MOI.Silent(), true)
true
```
