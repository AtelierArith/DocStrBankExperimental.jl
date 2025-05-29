```
similar(x::MatElem{T}, R::NCRing, r::Int, c::Int) where T <: NCRingElement
similar(x::MatElem{T}, R::NCRing) where T <: NCRingElement
similar(x::MatElem{T}, r::Int, c::Int) where T <: NCRingElement
similar(x::MatElem{T}) where T <: NCRingElement
```

与えられた環と次元に対して初期化されていない行列を作成し、与えられたソース行列 `x` に基づいてデフォルトを設定します。
