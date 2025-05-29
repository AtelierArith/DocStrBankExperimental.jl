```
lower_boundary_indices(domain::CartesianIndices{N}, axis::Int, n::Int) where {N}
```

与えられたCartesianIndicesから、指定された`axis`に沿って`n`のオフセットでのみ下限境界インデックスを抽出します。

# 例

```julia
julia> domain = CartesianIndices((1:10, 4:8))
CartesianIndices((1:10, 4:8))

julia> lower_boundary_indices(domain, 2, 0) # axis 2の最初のインデックスを選択
CartesianIndices((1:10, 4:4))
```
