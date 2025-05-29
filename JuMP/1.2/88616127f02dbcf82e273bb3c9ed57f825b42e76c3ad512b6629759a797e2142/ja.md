```
list_of_constraint_types(model::Model)::Vector{Tuple{Type,Type}}
```

モデルに対して、`all_constraints(model, F, S)` が非空リストを返すような形 `(F, S)` のタプルのリストを返します。ここで `F` は JuMP 関数型で、`S` は MOI セット型です。

# 例

```jldoctest; setup=:(using JuMP)
julia> model = Model();

julia> @variable(model, x >= 0, Bin);

julia> @constraint(model, 2x <= 1);

julia> list_of_constraint_types(model)
3-element Array{Tuple{Type,Type},1}:
 (GenericAffExpr{Float64,VariableRef}, MathOptInterface.LessThan{Float64})
 (VariableRef, MathOptInterface.GreaterThan{Float64})
 (VariableRef, MathOptInterface.ZeroOne)
```

## パフォーマンスに関する考慮事項

関数とセット型のリストを反復処理することは、型が不安定な操作です。関数バリアの使用を検討してください。詳細については、ドキュメントの [拡張のためのパフォーマンスのヒント](@ref) セクションを参照してください。
