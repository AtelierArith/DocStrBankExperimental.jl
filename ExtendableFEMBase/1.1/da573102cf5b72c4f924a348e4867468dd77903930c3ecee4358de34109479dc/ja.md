```
function QuadratureRule{T,ET}(order::Int) where {T<:Real, ET <: Parallelepiped3D}
```

指定された次数のParallelepiped3D上の数値積分ルールを構築します。
