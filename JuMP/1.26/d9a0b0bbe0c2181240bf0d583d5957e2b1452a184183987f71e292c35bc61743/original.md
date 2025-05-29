```
num_constraints(model::GenericModel, function_type, set_type)::Int64
```

Return the number of constraints currently in the model where the function has type `function_type` and the set has type `set_type`.

See also [`list_of_constraint_types`](@ref) and [`all_constraints`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 0, Bin);

julia> @variable(model, y);

julia> @constraint(model, y in MOI.GreaterThan(1.0));

julia> @constraint(model, y <= 1.0);

julia> @constraint(model, 2x <= 1);

julia> num_constraints(model, VariableRef, MOI.GreaterThan{Float64})
2

julia> num_constraints(model, VariableRef, MOI.ZeroOne)
1

julia> num_constraints(model, AffExpr, MOI.LessThan{Float64})
2
```
