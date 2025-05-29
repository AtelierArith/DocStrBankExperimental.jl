```
BlockArray(::UndefBlocksInitializer, ::Type{R}, block_sizes::Vararg{AbstractVector{<:Integer}, N}) where {N,R<:AbstractArray{<:Any,N}}
```

ブロックタイプ `R` から初期化されていないブロックを持つ `N` 次元の `BlockArray` を構築します。サイズは `block_sizes` によって定義されます。各ブロックはアクセスする前に **必ず** 割り当てられなければなりません。

# 例

```jldoctest
julia> B = BlockArray(undef_blocks, Matrix{Float64}, [1,3], [2,2])
2×2-blocked 4×4 BlockMatrix{Float64}:
 #undef  #undef  │  #undef  #undef
 ────────────────┼────────────────
 #undef  #undef  │  #undef  #undef
 #undef  #undef  │  #undef  #undef
 #undef  #undef  │  #undef  #undef

julia> typeof(blocks(B))
Matrix{Matrix{Float64}} (alias for Array{Array{Float64, 2}, 2})

julia> using SparseArrays

julia> B = BlockArray(undef_blocks, SparseMatrixCSC{Float64,Int}, [1,3], [2,2]);

julia> typeof(blocks(B))
Matrix{SparseMatrixCSC{Float64, Int64}} (alias for Array{SparseMatrixCSC{Float64, Int64}, 2})
```

[`undef_blocks`](@ref) や [`UndefBlocksInitializer`](@ref) も参照してください。
