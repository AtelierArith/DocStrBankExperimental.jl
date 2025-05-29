```
get_optimizer_attribute(model, name::String)
```

Return the value associated with the solver-specific attribute named `name`.

Note that this is equivalent to `get_optimizer_attribute(model, MOI.RawOptimizerAttribute(name))`.

## Example

```julia
get_optimizer_attribute(model, "SolverSpecificAttributeName")
```

See also: [`set_optimizer_attribute`](@ref), [`set_optimizer_attributes`](@ref).
