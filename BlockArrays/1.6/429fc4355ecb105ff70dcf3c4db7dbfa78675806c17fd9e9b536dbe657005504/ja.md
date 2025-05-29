```
BlockArray{T}(::UndefBlocksInitializer, block_sizes::Vararg{AbstractVector{<:Integer}, N}) where {T,N}
```

初期化されていないブロックを持つ `N` 次元の `BlockArray` を構築します。ブロックの型は `Array{T,N}` で、サイズは `block_sizes` によって定義されます。各ブロックはアクセスする前に**必ず**割り当てられなければなりません。

# 例

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

julia> B[Block(1)] .= 2 # エラー、ブロックがまだ割り当てられていないため
ERROR: UndefRefError: access to undefined reference
[...]

julia> B[Block(1)] = [1]; # ブロックに配列を割り当てる

julia> B[Block(2)] = [2,3];

julia> B
2-blocked 3-element BlockVector{Int8}:
 1
 ─
 2
 3
```

他にも [`undef_blocks`](@ref), [`UndefBlocksInitializer`](@ref) を参照してください。
