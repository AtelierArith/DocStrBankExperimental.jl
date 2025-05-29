```
ketbra(irow, icol, size)
```

`size`次元ベクトル空間に作用する行列を返します。`irow`、`icol` = 1, 2, ..., `size`。行列は、位置（`irow`、`icol`）に1に等しい単一の非ゼロ要素で構成されています。

# 例

```jldoctest; setup = :(using QSWalk)
julia> ketbra(1, 2, 3)
3×3 SparseArrays.SparseMatrixCSC{Int64,Int64} with 1 stored entry:
  [1, 2]  =  1

```
