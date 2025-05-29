```
ket(index, size)
```

`size`次元ベクトル空間における`index`-番目の基底（列）ベクトルを返します。Juliaのインデックスに従って、`index` = 1, 2, ..., `size`です。

# 例

```jldoctest; setup = :(using QSWalk)
julia> ket(1, 2)
2-element SparseArrays.SparseVector{Int64,Int64} with 1 stored entry:
  [1]  =  1
```
