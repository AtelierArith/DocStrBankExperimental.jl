```
all_constraints(model::Model, function_type, set_type)::Vector{<:ConstraintRef}
```

Return a list of all constraints currently in the model where the function has type `function_type` and the set has type `set_type`. The constraints are ordered by creation time.

See also [`list_of_constraint_types`](@ref) and [`num_constraints`](@ref).

# Example

```jldoctest; setup=:(using JuMP)
julia> model = Model();

julia> @variable(model, x >= 0, Bin);

julia> @constraint(model, 2x <= 1);

julia> all_constraints(model, VariableRef, MOI.GreaterThan{Float64})
1-element Array{ConstraintRef{Model,MathOptInterface.ConstraintIndex{MathOptInterface.VariableIndex,MathOptInterface.GreaterThan{Float64}},ScalarShape},1}:
 x ≥ 0.0

julia> all_constraints(model, VariableRef, MOI.ZeroOne)
1-element Array{ConstraintRef{Model,MathOptInterface.ConstraintIndex{MathOptInterface.VariableIndex,MathOptInterface.ZeroOne},ScalarShape},1}:
 x binary

julia> all_constraints(model, AffExpr, MOI.LessThan{Float64})
1-element Array{ConstraintRef{Model,MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64},MathOptInterface.LessThan{Float64}},ScalarShape},1}:
 2 x ≤ 1.0
```
