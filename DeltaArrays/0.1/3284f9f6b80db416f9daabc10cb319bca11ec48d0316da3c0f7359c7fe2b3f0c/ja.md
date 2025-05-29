```
DeltaArray(A::AbstractArray)
```

`A`の対角線から配列を構築します。

# 例

```jldoctest julia> A = reshape(1:16, 2, 2, 2, 2) 2×2×2×2 reshape(::UnitRange{Int64}, 2, 2, 2, 2) with eltype Int64: [:, :, 1, 1] =  1  3  2  4

[:, :, 2, 1] =  5  7  6  8

[:, :, 1, 2] =   9  11  10  12

[:, :, 2, 2] =  13  15  14  16

julia> DeltaArray(A) 2×2 DeltaArray{Int64, 2, Vector{Int64}}:  1   0  0  16

julia> delta(A) 2-element Vector{Int64}:   1  16
```
