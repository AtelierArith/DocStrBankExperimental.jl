```
step!(model::ABM)
```

`model`のシミュレーションステップを1回実行します。連続時間モデルの場合、これは次のイベントまでモデルを実行し、それを実行することを意味します。

```
step!(model::ABM, t::Real)
```

現在のモデル時間からの時間差が`≥ t`になるまでモデルを前進させます。つまり、モデルを少なくとも`t`時間前進させます。[`StandardABM`](@ref)のような離散時間モデルでは、`t`は整数でなければならず、モデルを*正確に* `t`ステップ進めます。

```
step!(model::ABM, f::Function)
```

`f(model, t)`が`true`を返すまでモデルを前進させます。ここで、`t`はモデルが進化した現在の時間量で、モデルの初期時間から始まります。

詳細は[Advanced stepping](@ref advanced_stepping)を参照してください。
