```
proj(index, size)
```

`size`次元ベクトル空間における`index`-th基底ベクトルへの射影を返します。`index`は1, 2, ..., `size`の値を取ります。これは`ketbra(index, index, size)`と同等です。

```jldoctest; setup = :(using QSWalk)
julia> proj(1, 2)
2×2 SparseArrays.SparseMatrixCSC{Int64,Int64} with 1 stored entry:
  [1, 1]  =  1
```
