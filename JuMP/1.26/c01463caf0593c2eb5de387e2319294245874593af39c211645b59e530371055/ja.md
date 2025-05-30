```
set_nonlinear_objective(
    model::Model,
    sense::MOI.OptimizationSense,
    expr::Expr,
)
```

`model`の非線形目的を`expr`の式に設定し、最適化の感覚`sense`を指定します。

この関数は、式`expr`がプログラム的に生成され、[`@NLobjective`](@ref)を使用できない場合に最も便利です。

!!! compat
    この関数はレガシー非線形インターフェースの一部です。 [非線形モデリング](@ref)に文書化されている新しい非線形インターフェースの使用を検討してください。


## 注意事項

  * 変数を式`expr`に直接補間する必要があります。
  * `Min`および`Max`の代わりに`MIN_SENSE`または`MAX_SENSE`を使用する必要があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> set_nonlinear_objective(model, MIN_SENSE, :($(x) + $(x)^2))
```
