```
all_constraints(model::GenericModel, function_type, set_type)::Vector{<:ConstraintRef}
```

モデル内のすべての制約のリストを返します。関数のタイプは `function_type` であり、セットのタイプは `set_type` です。制約は作成時間順に並べられます。

[`list_of_constraint_types`](@ref) および [`num_constraints`](@ref) も参照してください。

## 例

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
