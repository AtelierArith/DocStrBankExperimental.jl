```
function QuadratureRule{T,ET}(order::Int) where {T<:Real, ET <: Triangle2D}
```

指定された次数のTriangle2D上の数値積分則を構築します。
