```
LogQuantArray(::Type{TUInt},A::AbstractArray{T,N};dims::Int) where {TUInt<:Unsigned,T,N}
```

配列 `A` の次元 `dims` に沿って、各要素に対して独立に対数量子化を行います。

# 戻り値

  * Vector{LogQuantArray}。
