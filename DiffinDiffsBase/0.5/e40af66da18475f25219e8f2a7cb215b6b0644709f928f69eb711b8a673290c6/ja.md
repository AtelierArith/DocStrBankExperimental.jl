```
ScaledArray{T,R,N,RA,P} <: AbstractArray{T,N}
```

範囲のインデックスとしてデータを格納する配列型。

# フィールド

  * `refs::RA<:AbstractArray{R,N}`: インデックスの配列。
  * `pool::P<:AbstractRange`: 配列によって格納されるすべての可能な値をカバーする範囲。
  * `invpool::Dict{T,R}`: 配列要素から`pool`のインデックスへのマップ。
