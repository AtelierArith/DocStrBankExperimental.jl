```
struct ScalarConstraint
```

スカラー制約のデータ。

詳細については、JuMPの制約の表現に関する[ドキュメント](@ref Constraints)を参照してください。

## フィールド

  * `.func`: フィールドは関数を表すJuMPオブジェクトを含みます
  * `.set`: フィールドはMOIセットを含みます

## 例

スカラー制約：

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @constraint(model, c, 2x <= 1)
c : 2 x ≤ 1

julia> object = constraint_object(c)
ScalarConstraint{AffExpr, MathOptInterface.LessThan{Float64}}(2 x, MathOptInterface.LessThan{Float64}(1.0))

julia> typeof(object)
ScalarConstraint{AffExpr, MathOptInterface.LessThan{Float64}}

julia> object.func
2 x

julia> object.set
MathOptInterface.LessThan{Float64}(1.0)
```
