```
PoincareSphere2Map(I, p, X, grid)
PoincareSphere2Map(I::IntensityMap, p, X)
PoincareSphere2Map(I, p, X, cache::AbstractCache)
```

Poincareパラメータ化を使用して偏光強度マップモデルを構築します。引数は次のとおりです。

  * `I` は各ピクセルのフラックスのグリッドです。
  * `p` は0と1の間の数のグリッドで、全体の分数偏光を表します。
  * `X` は、各要素がPoincare球上の点を表す3つの数からなるグリッドであり、X[1,1]は `||X[1,1]|| == 1` となるNTuple{3}です。
  * `grid` は強度マップのピクセルの位置を示す次元グリッドです。

!!! note
    `I` が `IntensityMap` の場合、`grid` は必要ありません。なぜなら、`I` に使用されたのと同じグリッドが偏光強度マップの構築に使用されるからです。代わりにキャッシュが渡されると、[`ContinuousImage`](@ref) オブジェクトが返されます。

