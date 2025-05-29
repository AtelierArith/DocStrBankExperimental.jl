```
StressLayout <: AbstractLayout
```

ストレス主要化に基づくレイアウトアルゴリズム。

### フィールド

  * `optimal_distance::Float64`: 頂点間の最適距離
  * `maxiter::Int`: 最大反復回数
  * `rtol::Float64`: 絶対許容誤差
  * `initial_locs`: 初期頂点位置
  * `mask`: 再配置する頂点のためのブールマスク
  * `meta::Dict{Symbol, Any}`: グラフ依存のメタ情報、含む

      * `initial_locs`: 初期頂点位置
      * `mask`: 再配置する頂点のためのブールマスク
