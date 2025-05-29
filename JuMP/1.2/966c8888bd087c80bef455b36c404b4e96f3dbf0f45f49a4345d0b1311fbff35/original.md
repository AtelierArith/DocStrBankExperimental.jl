```
set_optimizer_attribute(model::Model, name::String, value)
```

Sets solver-specific attribute identified by `name` to `value`.

Note that this is equivalent to `set_optimizer_attribute(model, MOI.RawOptimizerAttribute(name), value)`.

## Example

```julia
set_optimizer_attribute(model, "SolverSpecificAttributeName", true)
```

See also: [`set_optimizer_attributes`](@ref), [`get_optimizer_attribute`](@ref).
