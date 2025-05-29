```
update_se_hessian!(
    partable::AbstractParameterTable,
    fit::SemFit;
    method = :finitediff)
```

Write hessian standard errors computed for `fit` to the `:se` column of `partable`

# Arguments

  * `method::Symbol`: how to compute the hessian, see [se_hessian](@ref) for more information.

# Examples
