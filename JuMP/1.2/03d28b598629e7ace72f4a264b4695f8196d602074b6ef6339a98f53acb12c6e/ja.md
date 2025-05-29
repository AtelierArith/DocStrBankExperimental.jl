```
set_nonlinear_objective(
    model::Model,
    sense::MOI.OptimizationSense,
    expr::Expr,
)
```

`model`の非線形目的を`expr`の式に設定し、最適化の感覚`sense`を指定します。

この関数は、式`expr`がプログラム的に生成され、[`@NLobjective`](@ref)を使用できない場合に最も便利です。

## 注意事項

  * 変数を式`expr`に直接補間する必要があります。
  * `Min`や`Max`の代わりに`MIN_SENSE`または`MAX_SENSE`を使用する必要があります。

## 例

```jldoctest; setup=:(using JuMP; model = Model(); @variable(model, x))
julia> set_nonlinear_objective(model, MIN_SENSE, :($(x) + $(x)^2))
```
