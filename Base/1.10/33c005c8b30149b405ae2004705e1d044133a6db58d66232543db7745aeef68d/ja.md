```
getindex(A, inds...)
```

配列 `A` のサブセットを `inds` によって指定された通りに返します。各 `ind` は、例えば `Int`、[`AbstractRange`](@ref)、または [`Vector`](@ref) である可能性があります。詳細については、[配列インデックス](@ref man-array-indexing) に関するマニュアルのセクションを参照してください。

# 例

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> getindex(A, 1)
1

julia> getindex(A, [2, 1])
2-element Vector{Int64}:
 3
 1

julia> getindex(A, 2:4)
3-element Vector{Int64}:
 3
 2
 4
```
