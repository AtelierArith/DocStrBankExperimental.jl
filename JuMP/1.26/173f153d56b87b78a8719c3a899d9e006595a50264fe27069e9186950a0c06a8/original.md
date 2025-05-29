```
num_nonlinear_constraints(model::GenericModel)
```

Returns the number of nonlinear constraints associated with the `model`.

!!! compat
    This function is part of the legacy nonlinear interface. Consider using the new nonlinear interface documented in [Nonlinear Modeling](@ref).


This function counts only the constraints added with [`@NLconstraint`](@ref) and [`add_nonlinear_constraint`](@ref). It does not count [`GenericNonlinearExpr`](@ref) constraints.
