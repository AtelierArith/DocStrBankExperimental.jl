```
objective_function_type(model::GenericModel)::AbstractJuMPScalar
```

Return the type of the objective function.

This function is equivalent to querying the [`MOI.ObjectiveFunctionType`](@ref) attribute.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @objective(model, Min, 2 * x + 1);

julia> objective_function_type(model)
AffExpr (alias for GenericAffExpr{Float64, GenericVariableRef{Float64}})
```
