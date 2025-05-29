```
BlockArray{T}(::UndefBlocksInitializer, block_sizes::Vararg{AbstractVector{<:Integer}, N}) where {T,N}
```

Construct a `N`-dim `BlockArray` with uninitialized blocks of type `Array{T,N}`, with sizes defined by `block_sizes`. Each block **must** be allocated before being accessed.

# Examples

```jldoctest
julia> B = BlockArray{Float64}(undef_blocks, [1,2], [1,2])
2×2-blocked 3×3 BlockMatrix{Float64}:
 #undef  │  #undef  #undef
 ────────┼────────────────
 #undef  │  #undef  #undef
 #undef  │  #undef  #undef

julia> typeof(blocks(B))
Matrix{Matrix{Float64}} (alias for Array{Array{Float64, 2}, 2})

julia> B = BlockArray{Int8}(undef_blocks, [1,2])
2-blocked 3-element BlockVector{Int8}:
 #undef
 ──────
 #undef
 #undef

julia> typeof(blocks(B))
Vector{Vector{Int8}} (alias for Array{Array{Int8, 1}, 1})

julia> B[Block(1)] .= 2 # errors, as the block is not allocated yet
ERROR: UndefRefError: access to undefined reference
[...]

julia> B[Block(1)] = [1]; # assign an array to the block

julia> B[Block(2)] = [2,3];

julia> B
2-blocked 3-element BlockVector{Int8}:
 1
 ─
 2
 3
```

See also [`undef_blocks`](@ref), [`UndefBlocksInitializer`](@ref)
