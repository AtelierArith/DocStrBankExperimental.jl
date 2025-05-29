```
ArrayQuantity{T,N}
```

型の和集合で、物理単位の有無にかかわらず、型 `T` の要素を持つ `N` 次元配列を表します。

`Union{Array{T,N}, AbstractQuantityArray{T,N}} where {T<:Number, N}` のエイリアスです。
