```
spatial_coordinate(ip::ScalarInterpolation, ξ::Vec, x::AbstractVector{<:Vec{sdim, T}})
```

与えられた数値点における空間座標を計算します。`x` にはセルのノード座標が含まれています。

座標は、幾何学的補間を使用して計算されます。$\mathbf{x} = \sum\limits_{i = 1}^n M_i (\mathbf{\xi}) \mathbf{\hat{x}}_i$
