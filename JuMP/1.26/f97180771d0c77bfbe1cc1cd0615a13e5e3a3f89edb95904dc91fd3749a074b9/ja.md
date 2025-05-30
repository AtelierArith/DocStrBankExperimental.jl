```
@build_constraint(constraint_expr)
```

`@constraint`(@ref)と同じ仕組みを使用して`ScalarConstraint`または`VectorConstraint`を構築しますが、制約をモデルに追加することはありません。

`x .<= 1`のようなブロードキャスト演算子を使用した制約もサポートされており、`ScalarConstraint`または`VectorConstraint`の配列を作成します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @build_constraint(2x >= 1)
ScalarConstraint{AffExpr, MathOptInterface.GreaterThan{Float64}}(2 x, MathOptInterface.GreaterThan{Float64}(1.0))
```

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> @build_constraint(x .>= 0)
2-element Vector{ScalarConstraint{AffExpr, MathOptInterface.GreaterThan{Float64}}}:
 ScalarConstraint{AffExpr, MathOptInterface.GreaterThan{Float64}}(x[1], MathOptInterface.GreaterThan{Float64}(-0.0))
 ScalarConstraint{AffExpr, MathOptInterface.GreaterThan{Float64}}(x[2], MathOptInterface.GreaterThan{Float64}(-0.0))
```
