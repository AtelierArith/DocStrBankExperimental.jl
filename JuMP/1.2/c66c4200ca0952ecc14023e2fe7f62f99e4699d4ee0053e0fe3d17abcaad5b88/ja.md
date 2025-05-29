```
all_constraints(model::Model, function_type, set_type)::Vector{<:ConstraintRef}
```

モデル内のすべての制約のリストを返します。関数のタイプは `function_type` であり、セットのタイプは `set_type` です。制約は作成時間順に並べられます。

[`list_of_constraint_types`](@ref) および [`num_constraints`](@ref) も参照してください。

# 例

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
