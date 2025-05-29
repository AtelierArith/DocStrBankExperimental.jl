```
set_variable_bound_info(vref, method::AbstractReformulationMethod)::Tuple{<:Number, <:Number}
```

Returns a tuple of the form `(lower_bound, upper_bound)` which are the bound information needed by  `method` to reformulate disjunctions. This only needs to be implemented for `methods` where  `requires_variable_bound_info(method) = true`. These bounds can later be accessed via  [`variable_bound_info`](@ref).
