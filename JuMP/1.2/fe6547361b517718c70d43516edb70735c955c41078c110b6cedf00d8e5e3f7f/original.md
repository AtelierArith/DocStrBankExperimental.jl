```
get_optimizer_attribute(
    model::Model, attr::MOI.AbstractOptimizerAttribute
)
```

Return the value of the solver-specific attribute `attr` in `model`.

## Example

```julia
get_optimizer_attribute(model, MOI.Silent())
```

See also: [`set_optimizer_attribute`](@ref), [`set_optimizer_attributes`](@ref).
