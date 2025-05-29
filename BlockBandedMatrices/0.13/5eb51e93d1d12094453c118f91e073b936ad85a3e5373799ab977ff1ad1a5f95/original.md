```
BlockBandedMatrix(A::Union{AbstractMatrix,UniformScaling},
                    rows::AbstractVector{Int}, cols::AbstractVector{Int},
                    (l,u)::NTuple{2,Int})
```

Return a `sum(rows) × sum(cols)` `BlockBandedMatrix`, with `rows` by `cols` blocks, with `(l,u)` as the block-bandwidth. The structural non-zero entries are equal to the corresponding indices of `A`.

# Examples

```jldoctest
julia> using LinearAlgebra, FillArrays

julia> l,u = 0,1; # block bandwidths

julia> nrowblk, ncolblk = 3, 3; # number of row/column blocks

julia> rows = 1:nrowblk; cols = 1:ncolblk; # block sizes

julia> BlockBandedMatrix(I, rows, cols, (l,u))
3×3-blocked 6×6 BlockBandedMatrix{Bool}:
 1  │  0  0  │  ⋅  ⋅  ⋅
 ───┼────────┼─────────
 ⋅  │  1  0  │  0  0  0
 ⋅  │  0  1  │  0  0  0
 ───┼────────┼─────────
 ⋅  │  ⋅  ⋅  │  1  0  0
 ⋅  │  ⋅  ⋅  │  0  1  0
 ⋅  │  ⋅  ⋅  │  0  0  1

julia> BlockBandedMatrix(Ones(sum(rows),sum(cols)), rows, cols, (l,u))
3×3-blocked 6×6 BlockBandedMatrix{Float64}:
 1.0  │  1.0  1.0  │   ⋅    ⋅    ⋅
 ─────┼────────────┼───────────────
  ⋅   │  1.0  1.0  │  1.0  1.0  1.0
  ⋅   │  1.0  1.0  │  1.0  1.0  1.0
 ─────┼────────────┼───────────────
  ⋅   │   ⋅    ⋅   │  1.0  1.0  1.0
  ⋅   │   ⋅    ⋅   │  1.0  1.0  1.0
  ⋅   │   ⋅    ⋅   │  1.0  1.0  1.0
```
