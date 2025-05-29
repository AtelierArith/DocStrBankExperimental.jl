```
add_nonlinear_constraint(model::Model, expr::Expr)
```

Julia式`ex`で記述された非線形制約を`model`に追加します。

この関数は、式`ex`がプログラム的に生成され、[`@NLconstraint`](@ref)を使用できない場合に最も便利です。

!!! compat
    この関数は、レガシー非線形インターフェースの一部です。[非線形モデリング](@ref)で文書化された新しい非線形インターフェースの使用を検討してください。


## 注意事項

  * 変数を式`expr`に直接補間する必要があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> add_nonlinear_constraint(model, :($(x) + $(x)^2 <= 1))
(x + x ^ 2.0) - 1.0 ≤ 0
```
