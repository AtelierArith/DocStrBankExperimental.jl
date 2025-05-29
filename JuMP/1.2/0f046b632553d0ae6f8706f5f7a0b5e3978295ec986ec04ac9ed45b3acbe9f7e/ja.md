```
@build_constraint(constraint_expr)
```

`ScalarConstraint`または`VectorConstraint`を[`@constraint`](@ref)と同じ仕組みを使って構築しますが、モデルに制約を追加することはありません。

`x .<= 1`のようなブロードキャスト演算子を使用した制約もサポートされており、`ScalarConstraint`または`VectorConstraint`の配列を作成します。

## 例

```jldoctest; setup = :(using JuMP)
model = Model();
@variable(model, x);
@build_constraint(2x >= 1)

# 出力
ScalarConstraint{GenericAffExpr{Float64,VariableRef},MathOptInterface.GreaterThan{Float64}}(2 x, MathOptInterface.GreaterThan{Float64}(1.0))
```
