```
all_constraints(
    model::GenericModel;
    include_variable_in_set_constraints::Bool,
)::Vector{ConstraintRef}
```

`model`内のすべての制約のリストを返します。

`include_variable_in_set_constraints == true`の場合、`VariableRef`制約（例えば、`VariableRef`-in-`Integer`）が含まれます。構造的制約のみを返すには（例えば、線形プログラムの制約行列の行）、`include_variable_in_set_constraints = false`を渡してください。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 0, Int);

julia> @constraint(model, 2x <= 1);

julia> @NLconstraint(model, x^2 <= 1);

julia> all_constraints(model; include_variable_in_set_constraints = true)
4-element Vector{ConstraintRef}:
 2 x ≤ 1
 x ≥ 0
 x integer
 x ^ 2.0 - 1.0 ≤ 0

julia> all_constraints(model; include_variable_in_set_constraints = false)
2-element Vector{ConstraintRef}:
 2 x ≤ 1
 x ^ 2.0 - 1.0 ≤ 0
```

## パフォーマンスに関する考慮事項

この関数は抽象的に型付けされたベクターを返すため、型が不安定であることに注意してください。パフォーマンスが問題である場合は、[`list_of_constraint_types`](@ref)と関数バリアを使用することを検討してください。詳細については、ドキュメントの[拡張のためのパフォーマンスのヒント](@ref)セクションを参照してください。
