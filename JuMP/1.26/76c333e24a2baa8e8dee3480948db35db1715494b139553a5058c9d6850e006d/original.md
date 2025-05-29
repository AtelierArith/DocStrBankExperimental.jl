```
all_nonlinear_constraints(model::GenericModel)
```

Return a vector of all nonlinear constraint references in the model in the order they were added to the model.

!!! compat
    This function is part of the legacy nonlinear interface. Consider using the new nonlinear interface documented in [Nonlinear Modeling](@ref).


This function returns only the constraints added with [`@NLconstraint`](@ref) and [`add_nonlinear_constraint`](@ref). It does not return [`GenericNonlinearExpr`](@ref) constraints.
