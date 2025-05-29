```
block_diagonal_matrix(R::NCRing, V::Vector{<:Matrix{T}}) where T <: NCRingElement
```

リング `R` 上にブロック対角行列を作成します。ブロックは `V` にある行列によって与えられます。エントリは作成時に `R` に強制変換されます。
