```
LogQuantArray(::Type{TUInt},A::AbstractArray{T,N},dim::Int) where {TUInt,T,N}
```

配列 A の次元 dim に沿って各要素を独立に対数量子化します。

# 引数

  * `TUInt`: 量子化された配列の型
  * `A`: 量子化する配列
  * `dim`: 量子化する次元

# 戻り値

  * 量子化された配列と元の範囲の最小値および最大値を含む Vector{LogQuantArray}。
