```
update_start!(partable::AbstractParameterTable, fit::SemFit)
update_start!(partable::AbstractParameterTable, model::AbstractSem, start_val; kwargs...)
```

Write starting values from `fit` or `start_val` to the `:start` column of `partable`.

# Arguments

  * `start_val`: either a vector of starting values or a function to compute starting values   from `model`
  * `kwargs...`: are passed to `start_val`
