```
upper_boundary_indices(domain::CartesianIndices{N}, axis::Int, n::Int) where {N}
```

与えられたCartesianIndicesを取り、指定された`axis`に沿って`n`のオフセットで上限境界インデックスのみを抽出します。

# 例

```julia
julia> domain = CartesianIndices((1:10, 4:8))
CartesianIndices((1:10, 4:8))

julia> upper_boundary_indices(domain, 2, 1)
CartesianIndices((1:10, 8:8))
```
