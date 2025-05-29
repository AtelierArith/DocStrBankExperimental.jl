```
num_constraints(model::Model, function_type, set_type)::Int64
```

モデル内の制約の数を返します。関数の型は `function_type` で、集合の型は `set_type` です。

関連情報としては [`list_of_constraint_types`](@ref) と [`all_constraints`](@ref) を参照してください。

# 例

```jldoctest; setup=:(using JuMP)
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
