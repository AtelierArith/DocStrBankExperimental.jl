```
BlockArray(::UndefBlocksInitializer, ::Type{R}, block_sizes::Vararg{AbstractVector{<:Integer}, N}) where {N,R<:AbstractArray{<:Any,N}}
```

Construct a `N`-dim `BlockArray` with uninitialized blocks from a block type `R`, with sizes defined by `block_sizes`. Each block **must** be allocated before being accessed.

# Examples

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

See also [`undef_blocks`](@ref), [`UndefBlocksInitializer`](@ref)
