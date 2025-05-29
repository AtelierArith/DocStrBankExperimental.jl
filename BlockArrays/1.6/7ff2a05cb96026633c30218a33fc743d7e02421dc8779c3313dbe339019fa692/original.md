```
undef_blocks
```

Alias for `UndefBlocksInitializer()`, which constructs an instance of the singleton type [`UndefBlocksInitializer`](@ref), used in block array initialization to indicate the array-constructor-caller would like an uninitialized block array.

# Examples

```jldoctest
julia> BlockArray(undef_blocks, Matrix{Float32}, [1,2], [3,2])
2×2-blocked 3×5 BlockMatrix{Float32}:
 #undef  #undef  #undef  │  #undef  #undef
 ────────────────────────┼────────────────
 #undef  #undef  #undef  │  #undef  #undef
 #undef  #undef  #undef  │  #undef  #undef
```
