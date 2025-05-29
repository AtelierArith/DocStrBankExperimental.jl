```
add_nonlinear_expression(model::Model, expr::Expr)
```

モデルに非線形式 `expr` を追加します。

この関数は、式 `expr` がプログラム的に生成され、[`@NLexpression`](@ref) を使用できない場合に最も便利です。

## 注意事項

  * 変数を式 `expr` に直接補間する必要があります。

## 例

```jldoctest; setup=:(using JuMP; model = Model(); @variable(model, x))
julia> add_nonlinear_expression(model, :($(x) + $(x)^2))
subexpression[1]: x + x ^ 2.0
```
