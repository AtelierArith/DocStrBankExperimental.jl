```
all_constraints(model::GenericModel, function_type, set_type)::Vector{<:ConstraintRef}
```

Return a list of all constraints currently in the model where the function has type `function_type` and the set has type `set_type`. The constraints are ordered by creation time.

See also [`list_of_constraint_types`](@ref) and [`num_constraints`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 0, Bin);

julia> @constraint(model, 2x <= 1);

julia> all_constraints(model, VariableRef, MOI.GreaterThan{Float64})
1-element Vector{ConstraintRef{Model, MathOptInterface.ConstraintIndex{MathOptInterface.VariableIndex, MathOptInterface.GreaterThan{Float64}}, ScalarShape}}:
 x ≥ 0

julia> all_constraints(model, VariableRef, MOI.ZeroOne)
1-element Vector{ConstraintRef{Model, MathOptInterface.ConstraintIndex{MathOptInterface.VariableIndex, MathOptInterface.ZeroOne}, ScalarShape}}:
 x binary

julia> all_constraints(model, AffExpr, MOI.LessThan{Float64})
1-element Vector{ConstraintRef{Model, MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64}, MathOptInterface.LessThan{Float64}}, ScalarShape}}:
 2 x ≤ 1
```
