```
bra(index, size)
```

`size`次元ベクトル空間における`index`-番目の基底行ベクトルを返します。`index` = 1, 2, ..., `size`です。

# 例

```jldoctest; setup = :(using QSWalk)
julia> bra(1, 2)
1×2 LinearAlgebra.Adjoint{Int64,SparseArrays.SparseVector{Int64,Int64}}:
 1  0
```
