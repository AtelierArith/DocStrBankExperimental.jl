```
VariablesConstrainedOnCreation <: AbstractVariable
```

Vector of variables `scalar_variables` constrained to belong to `set`. Adding this variable can be thought as doing:

```julia
function JuMP.add_variable(model::Model, variable::JuMP.VariablesConstrainedOnCreation, names)
    var_refs = JuMP.add_variable.(model, variable.scalar_variables,
                                  JuMP.vectorize(names, variable.shape))
    JuMP.add_constraint(model, JuMP.VectorConstraint(var_refs, variable.set))
    return JuMP.reshape_vector(var_refs, variable.shape)
end
```

but adds the variables with `MOI.add_constrained_variables(model, variable.set)` instead. See [the MOI documentation](https://jump.dev/MathOptInterface.jl/v0.9.3/apireference/#Variables-1) for the difference between adding the variables with `MOI.add_constrained_variables` and adding them with `MOI.add_variables` and adding the constraint separately.
