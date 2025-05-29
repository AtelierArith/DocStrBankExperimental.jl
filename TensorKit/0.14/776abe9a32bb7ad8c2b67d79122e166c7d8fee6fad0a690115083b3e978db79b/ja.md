```
flip(V::S) where {S<:ElementarySpace} -> S
```

`dual(V)`と同じ値の[`isdual`](@ref)を持つ、しかし`dual(V)`ではなく`V`に同型の型`S`の単一ベクトル空間を返します。空間`flip(V)`と`dual(V)`は、[`GradedSpace{I}`](@ref)の場合のみ異なります。
