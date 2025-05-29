```
value(con_ref::ConstraintRef; result::Int = 1)
```

Return the primal value of constraint `con_ref` associated with result index `result` of the most-recent solution returned by the solver.

That is, if `con_ref` is the reference of a constraint `func`-in-`set`, it returns the value of `func` evaluated at the value of the variables (given by [`value(::GenericVariableRef)`](@ref)).

Use [`primal_status`](@ref) to check if a result exists before asking for values.

See also: [`result_count`](@ref).

## Note

For scalar constraints, the constant is moved to the `set` so it is not taken into account in the primal value of the constraint. For instance, the constraint `@constraint(model, 2x + 3y + 1 == 5)` is transformed into `2x + 3y`-in-`MOI.EqualTo(4)` so the value returned by this function is the evaluation of `2x + 3y`.
