```
squared_errors(g::BVHGraph, f::Integer)
```

与えられたフレーム `f` に対して、頂点の現在の位置と保存された位置の二乗差の合計を計算します。

すべてのフレームに対して位置を持つ頂点のみが考慮されます。

参照: [`total_squared_errors`](@ref)
