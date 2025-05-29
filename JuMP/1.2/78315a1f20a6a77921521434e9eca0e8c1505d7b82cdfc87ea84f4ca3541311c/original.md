```
set_optimizer_attribute(
    model::Model,
    attr::MOI.AbstractOptimizerAttribute,
    value,
)
```

Set the solver-specific attribute `attr` in `model` to `value`.

## Example

```julia
set_optimizer_attribute(model, MOI.Silent(), true)
```

See also: [`set_optimizer_attributes`](@ref), [`get_optimizer_attribute`](@ref).
