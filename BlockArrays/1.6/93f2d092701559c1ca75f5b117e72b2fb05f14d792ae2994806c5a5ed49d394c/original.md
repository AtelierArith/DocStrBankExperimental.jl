```
BlockArray{T}(::UndefInitializer, block_sizes::Vararg{AbstractVector{<:Integer}, N}) where {T, N}
```

Construct a `N`-dim `BlockArray` with blocks of type `Array{T,N}`, with sizes defined by `block_sizes`. The blocks are allocated using `similar`, and the elements in each block are therefore unitialized.

# Examples

```jldoctest
julia> B = BlockArray{Int8}(undef, [1,2]);

julia> B[Block(1)] .= 2;

julia> B[Block(2)] .= 3;

julia> B
2-blocked 3-element BlockVector{Int8}:
 2
 ─
 3
 3
```
