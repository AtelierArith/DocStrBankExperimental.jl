```
function QuadratureRule{T,ET}(order::Int) where {T<:Real, ET <: AbstractElementGeometry0D}
```

指定された次数の0D数値積分ルールを構築します（常に点評価）。
