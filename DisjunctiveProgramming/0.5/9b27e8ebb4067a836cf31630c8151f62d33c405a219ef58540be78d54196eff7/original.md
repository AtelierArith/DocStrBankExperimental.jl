```
requires_variable_bound_info(method::AbstractReformulationMethod)::Bool
```

Return a `Bool` whether `method` requires variable bound information accessed  via [`variable_bound_info`](@ref). This should be extended for new  [`AbstractReformulationMethod`](@ref) methods if needed (defaults to `false`).  If a new method does require variable bound information, then  [`set_variable_bound_info`](@ref) should also be extended.
