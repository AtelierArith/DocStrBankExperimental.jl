```
VariableConstrainedOnCreation <: AbstractVariable
```

Variable `scalar_variables` constrained to belong to `set`.

Adding this variable can be understood as doing:

```julia
function JuMP.add_variable(
    model::GenericModel,
    variable::VariableConstrainedOnCreation,
    names,
)
    var_ref = add_variable(model, variable.scalar_variable, name)
    add_constraint(model, VectorConstraint(var_ref, variable.set))
    return var_ref
end
```

but adds the variables with `MOI.add_constrained_variable(model, variable.set)` instead.
