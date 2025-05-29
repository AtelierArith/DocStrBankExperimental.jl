```
struct RegularGrid{N,B,R,S,T} <: AbstractGrid{N,B,T}
```

各パラメータが等間隔で配置されたグリッドの構造体です。

# フィールド

  * `lower_bounds::B`: 各パラメータの下限。
  * `upper_bounds::B`: 各パラメータの上限。
  * `resolution::R`: 各パラメータのグリッドポイントの数。`R <: Number` の場合、各パラメータに対して同じ数のグリッドポイントが使用されます。
  * `step_sizes::S`: 各パラメータのグリッド間隔。

# コンストラクタ

`RegularGrid(lower_bounds, upper_bounds, resolution)` を使用して `RegularGrid` を構築できます。
