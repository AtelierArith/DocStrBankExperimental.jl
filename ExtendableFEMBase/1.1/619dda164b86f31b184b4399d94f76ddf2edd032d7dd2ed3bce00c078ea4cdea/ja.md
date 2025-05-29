```
function QuadratureRule{T,ET}(order::Int) where {T<:Real, ET <: Parallelogram2D}
```

指定された次数のParallelogram2D上の数値積分ルールを構築します。
