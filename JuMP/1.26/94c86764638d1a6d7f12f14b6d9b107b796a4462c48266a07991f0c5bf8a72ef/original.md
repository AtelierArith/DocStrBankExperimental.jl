```
VariablesConstrainedOnCreation <: AbstractVariable
```

Vector of variables `scalar_variables` constrained to belong to `set`. Adding this variable can be thought as doing:

```julia
function JuMP.add_variable(
    model::GenericModel,
    variable::VariablesConstrainedOnCreation,
    names,
)
    v_names = vectorize(names, variable.shape)
    var_refs = add_variable.(model, variable.scalar_variables, v_names)
    add_constraint(model, VectorConstraint(var_refs, variable.set))
    return reshape_vector(var_refs, variable.shape)
end
```

but adds the variables with `MOI.add_constrained_variables(model, variable.set)` instead. See [the MOI documentation](https://jump.dev/MathOptInterface.jl/v0.9.3/apireference/#Variables-1) for the difference between adding the variables with `MOI.add_constrained_variables` and adding them with `MOI.add_variables` and adding the constraint separately.
