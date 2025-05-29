```
BlockBandedMatrix(A::AbstractMatrix, (l,u)::NTuple{2,Int})
```

Return a `BlockBandedMatrix` with block-bandwidths `(l,u)`, where the structural non-zero blocks correspond to those of `A`.

Examples

```jldoctest
julia> using BlockArrays

julia> B = BlockArray(ones(6,6), 1:3, 1:3);

julia> BlockBandedMatrix(B, (1,1))
3×3-blocked 6×6 BlockBandedMatrix{Float64}:
 1.0  │  1.0  1.0  │   ⋅    ⋅    ⋅
 ─────┼────────────┼───────────────
 1.0  │  1.0  1.0  │  1.0  1.0  1.0
 1.0  │  1.0  1.0  │  1.0  1.0  1.0
 ─────┼────────────┼───────────────
  ⋅   │  1.0  1.0  │  1.0  1.0  1.0
  ⋅   │  1.0  1.0  │  1.0  1.0  1.0
  ⋅   │  1.0  1.0  │  1.0  1.0  1.0
```
