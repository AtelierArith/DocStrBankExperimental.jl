```
current_parameters(ds::DynamicalSystem) → p
```

Return the current parameter container of `ds`. This is mutated in functions that need to evolve `ds` across a parameter range.

See also [`initial_parameters`](@ref), [`current_parameter`](@ref), [`set_parameter!`](@ref).
