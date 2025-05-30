```
ridge2d(bs::MixedModelBootstrap; ptype=:β, kwargs...)
ridge2d!(f::Union{GridLayoutBase.GridLayout, GridLayoutBase.GridPosition, GridLayoutBase.GridSubposition, Makie.Figure}, bs::MixedModelBootstrap; ptype=:β)
```

ブートストラップサンプルの上に重ねられた密度を持つペアワイズ二変量散布図をプロットします。

`ptype`は調べるパラメータのセットを指定します。例： `:β`, `:σ`, `:ρ`。

ミューテーションメソッドは元のオブジェクトを返します。
