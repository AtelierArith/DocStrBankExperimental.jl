```
set_attribute(model::GenericModel, attr::MOI.AbstractModelAttribute, value)
set_attribute(x::GenericVariableRef, attr::MOI.AbstractVariableAttribute, value)
set_attribute(cr::ConstraintRef, attr::MOI.AbstractConstraintAttribute, value)
```

Set the value of a solver-specifc attribute `attr` to `value`.

This is equivalent to calling [`MOI.set`](@ref) with the associated MOI model and, for variables and constraints, with the associated [`MOI.VariableIndex`](@ref) or [`MOI.ConstraintIndex`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> @constraint(model, c, 2 * x <= 1)
c : 2 x ≤ 1

julia> set_attribute(model, MOI.Name(), "model_new")

julia> set_attribute(x, MOI.VariableName(), "x_new")

julia> set_attribute(c, MOI.ConstraintName(), "c_new")
```
