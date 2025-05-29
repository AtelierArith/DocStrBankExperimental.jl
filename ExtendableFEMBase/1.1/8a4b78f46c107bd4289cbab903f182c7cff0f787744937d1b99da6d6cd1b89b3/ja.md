```
function QuadratureRule{T,ET}(order::Int) where {T<:Real, ET <: Tetrahedron3D}
```

指定された次数のTetrahedron3D上の数値積分ルールを構築します。
