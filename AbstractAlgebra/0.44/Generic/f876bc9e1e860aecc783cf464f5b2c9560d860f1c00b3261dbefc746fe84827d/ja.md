```
combine_like_terms!(a::MPoly{T}) where T <: RingElement
```

ゼロ項を削除し、同じ指数ベクトルを持つ隣接項を結合します。修正された多項式が返されます。
