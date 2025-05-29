```
get_attribute(model::GenericModel, attr::MOI.AbstractModelAttribute)
get_attribute(x::GenericVariableRef, attr::MOI.AbstractVariableAttribute)
get_attribute(cr::ConstraintRef, attr::MOI.AbstractConstraintAttribute)
```

Get the value of a solver-specifc attribute `attr`.

This is equivalent to calling [`MOI.get`](@ref) with the associated MOI model and, for variables and constraints, with the associated [`MOI.VariableIndex`](@ref) or [`MOI.ConstraintIndex`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> @constraint(model, c, 2 * x <= 1)
c : 2 x ≤ 1

julia> get_attribute(model, MOI.Name())
""

julia> get_attribute(x, MOI.VariableName())
"x"

julia> get_attribute(c, MOI.ConstraintName())
"c"
```
