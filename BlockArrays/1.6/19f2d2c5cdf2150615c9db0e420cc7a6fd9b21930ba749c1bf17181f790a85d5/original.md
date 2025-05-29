```
blocks(a::AbstractArray{T,N}) :: AbstractArray{<:AbstractArray{T,N},N}
```

Return the array-of-arrays view to `a` such that

```
blocks(a)[i₁, i₂, ..., iₙ] == a[Block(i₁), Block(i₂), ..., Block(iₙ)]
```

This function does not copy the blocks and give a mutable viwe to the original array.  This is an "inverse" of [`mortar`](@ref).

# Examples

```jldoctest
julia> bs1 = permutedims(reshape([
               1ones(1, 3), 2ones(1, 2),
               3ones(2, 3), 4ones(2, 2),
           ], (2, 2)))
2×2 Matrix{Matrix{Float64}}:
 [1.0 1.0 1.0]               [2.0 2.0]
 [3.0 3.0 3.0; 3.0 3.0 3.0]  [4.0 4.0; 4.0 4.0]

julia> a = mortar(bs1)
2×2-blocked 3×5 BlockMatrix{Float64}:
 1.0  1.0  1.0  │  2.0  2.0
 ───────────────┼──────────
 3.0  3.0  3.0  │  4.0  4.0
 3.0  3.0  3.0  │  4.0  4.0

julia> bs2 = blocks(a)
2×2 Matrix{Matrix{Float64}}:
 [1.0 1.0 1.0]               [2.0 2.0]
 [3.0 3.0 3.0; 3.0 3.0 3.0]  [4.0 4.0; 4.0 4.0]

julia> bs1 == bs2
true

julia> bs2[1, 1] .*= 100;

julia> a  # in-place mutation is reflected to the block array
2×2-blocked 3×5 BlockMatrix{Float64}:
 100.0  100.0  100.0  │  2.0  2.0
 ─────────────────────┼──────────
   3.0    3.0    3.0  │  4.0  4.0
   3.0    3.0    3.0  │  4.0  4.0
```
