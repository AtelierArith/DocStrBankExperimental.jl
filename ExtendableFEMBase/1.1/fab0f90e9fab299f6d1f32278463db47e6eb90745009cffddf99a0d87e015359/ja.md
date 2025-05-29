```
function QuadratureRule{T,ET}(order::Int) where {T<:Real, ET <: AbstractElementGeometry1D}
```

指定された次数の1D数値積分ルールを構築します。
