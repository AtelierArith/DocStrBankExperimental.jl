```
list_of_constraint_types(model::GenericModel)::Vector{Tuple{Type,Type}}
```

`(F, S)`の形式のタプルのリストを返します。ここで、`F`はJuMP関数型で、`S`はMOIセット型です。`all_constraints(model, F, S)`が空でないリストを返すようなものです。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 0, Bin);

julia> @constraint(model, 2x <= 1);

julia> list_of_constraint_types(model)
3-element Vector{Tuple{Type, Type}}:
 (AffExpr, MathOptInterface.LessThan{Float64})
 (VariableRef, MathOptInterface.GreaterThan{Float64})
 (VariableRef, MathOptInterface.ZeroOne)
```

## パフォーマンスに関する考慮事項

関数型とセット型のリストを反復処理することは、型が不安定な操作です。関数バリアの使用を検討してください。詳細については、ドキュメントの[拡張のためのパフォーマンスのヒント](@ref)セクションを参照してください。
