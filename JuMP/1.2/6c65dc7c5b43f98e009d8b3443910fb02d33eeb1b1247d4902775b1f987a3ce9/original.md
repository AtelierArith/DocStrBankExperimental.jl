```
VariablesConstrainedOnCreation <: AbstractVariable
```

Variable `scalar_variables` constrained to belong to `set`. Adding this variable can be understood as doing:

```julia
function JuMP.add_variable(model::Model, variable::JuMP.VariableConstrainedOnCreation, names)
    var_ref = JuMP.add_variable(model, variable.scalar_variable, name)
    JuMP.add_constraint(model, JuMP.VectorConstraint(var_ref, variable.set))
    return var_ref
end
```

but adds the variables with `MOI.add_constrained_variable(model, variable.set)` instead. See [the MOI documentation](https://jump.dev/MathOptInterface.jl/v0.9.3/apireference/#Variables-1) for the difference between adding the variables with `MOI.add_constrained_variable` and adding them with `MOI.add_variable` and adding the constraint separately.
