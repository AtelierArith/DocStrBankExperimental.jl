```
set_start_values(
    model::GenericModel;
    variable_primal_start::Union{Nothing,Function} = value,
    constraint_primal_start::Union{Nothing,Function} = value,
    constraint_dual_start::Union{Nothing,Function} = dual,
    nonlinear_dual_start::Union{Nothing,Function} = nonlinear_dual_start_value,
)
```

Set the primal and dual starting values in `model` using the functions provided.

If any keyword argument is `nothing`, the corresponding start value is skipped.

If the optimizer does not support setting the starting value, the value will be skipped.

## `variable_primal_start`

This function controls the primal starting solution for the variables. It is equivalent to calling [`set_start_value`](@ref) for each variable, or setting the [`MOI.VariablePrimalStart`](@ref) attribute.

If it is a function, it must have the form `variable_primal_start(x::VariableRef)` that maps each variable `x` to the starting primal value.

The default is [`value`](@ref).

## `constraint_primal_start`

This function controls the primal starting solution for the constraints. It is equivalent to calling [`set_start_value`](@ref) for each constraint, or setting the [`MOI.ConstraintPrimalStart`](@ref) attribute.

If it is a function, it must have the form `constraint_primal_start(ci::ConstraintRef)` that maps each constraint `ci` to the starting primal value.

The default is [`value`](@ref).

## `constraint_dual_start`

This function controls the dual starting solution for the constraints. It is equivalent to calling [`set_dual_start_value`](@ref) for each constraint, or setting the [`MOI.ConstraintDualStart`](@ref) attribute.

If it is a function, it must have the form `constraint_dual_start(ci::ConstraintRef)` that maps each constraint `ci` to the starting dual value.

The default is [`dual`](@ref).

## `nonlinear_dual_start`

This function controls the dual starting solution for the nonlinear constraints It is equivalent to calling [`set_nonlinear_dual_start_value`](@ref).

If it is a function, it must have the form `nonlinear_dual_start(model::GenericModel)` that returns a vector corresponding to the dual start of the constraints.

The default is [`nonlinear_dual_start_value`](@ref).
