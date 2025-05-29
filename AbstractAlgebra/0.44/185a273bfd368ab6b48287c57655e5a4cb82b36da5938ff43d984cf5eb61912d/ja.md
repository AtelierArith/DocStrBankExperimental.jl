```
zero(x::MatElem{T}, R::NCRing, r::Int, c::Int) where T <: NCRingElement
zero(x::MatElem{T}, r::Int, c::Int) where T <: NCRingElement
zero(x::MatElem{T}, R::NCRing) where T <: NCRingElement
zero(x::MatElem{T}) where T <: NCRingElement
```

与えられた環と次元に対してゼロ行列を作成し、デフォルトは与えられたソース行列 `x` に基づいています。
