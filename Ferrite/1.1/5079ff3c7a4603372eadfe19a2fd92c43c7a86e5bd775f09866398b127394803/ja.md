```
allocate_matrix(sp::SparsityPattern)
```

スパースパターン `sp` からタイプ `SparseMatrixCSC{Float64, Int}` のスパース行列を割り当てます。

このメソッドは、同等の [`allocate_matrix(SparseMatrixCSC{Float64, Int}, sp)`](@ref allocate_matrix(::Type{S}, sp::Ferrite.AbstractSparsityPattern) where {Tv, Ti, S <: SparseMatrixCSC{Tv, Ti}}) の短縮形です。
