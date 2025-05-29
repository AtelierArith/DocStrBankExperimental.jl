```
TensorIndices{<:Tuple}
```

いくつかの [`TensorSpace`](@ref) のための多次元矩形インデックス範囲。

# 例

```jldoctest
julia> TensorIndices((0:2, -1:1))
TensorIndices{Tuple{UnitRange{Int64}, UnitRange{Int64}}}((0:2, -1:1))

julia> indices(Taylor(2) ⊗ Fourier(1, 1.0))
TensorIndices{Tuple{UnitRange{Int64}, UnitRange{Int64}}}((0:2, -1:1))
```
