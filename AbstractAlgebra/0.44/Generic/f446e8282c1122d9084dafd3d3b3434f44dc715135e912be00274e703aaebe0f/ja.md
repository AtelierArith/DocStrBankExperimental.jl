```
isless(a::MPoly{T}, b::MPoly{T}) where {T <: RingElement}
```

単項式 $a$ が親環の単項式順序に関して単項式 $b$ よりも小さい場合、`true` を返します。
