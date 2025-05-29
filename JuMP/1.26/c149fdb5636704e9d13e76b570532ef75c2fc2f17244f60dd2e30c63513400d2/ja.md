```
delete(model::GenericModel, con_refs::Vector{<:ConstraintRef})
```

`con_refs` に関連付けられた制約をモデル `model` から削除します。

ソルバーは、同じ具体的な型の複数の制約を削除するための特化したメソッドを実装することがあります。これらのメソッドは、単一の制約 `delete` メソッドを繰り返し呼び出すよりも効率的である可能性があります。

参照: [`unregister`](@ref)

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:3]);

julia> @constraint(model, c, 2 * x .<= 1)
3-element Vector{ConstraintRef{Model, MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64}, MathOptInterface.LessThan{Float64}}, ScalarShape}}:
 c : 2 x[1] ≤ 1
 c : 2 x[2] ≤ 1
 c : 2 x[3] ≤ 1

julia> delete(model, c)

julia> unregister(model, :c)

julia> print(model)
Feasibility
Subject to

julia> model[:c]
ERROR: KeyError: key :c not found
Stacktrace:
[...]
```
