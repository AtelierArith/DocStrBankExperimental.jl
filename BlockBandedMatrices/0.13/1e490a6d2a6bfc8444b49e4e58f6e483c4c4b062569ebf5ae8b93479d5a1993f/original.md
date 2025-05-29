```
BandedBlockBandedMatrix(M::Union{UniformScaling,AbstractMatrix},
                           rows, cols, (l, u), (λ, μ))
```

Return a `sum(rows) × sum(cols)` banded-block-banded matrix `A`, with block-bandwidths `(l,u)` and where `A[Block(K,J)]` is a `BandedMatrix` of size `rows[K]`×`cols[J]` with bandwidths `(λ,μ)`. The structural non-zero elements of the returned matrix corresponds to those of `M`.

# Examples

```jldoctest
julia> using LinearAlgebra, FillArrays

julia> BandedBlockBandedMatrix(I, [3,4,3], [3,4,3], (1,1), (1,1))
3×3-blocked 10×10 BandedBlockBandedMatrix{Bool} with block-bandwidths (1, 1) and sub-block-bandwidths block-bandwidths (1, 1):
 1  0  ⋅  │  0  0  ⋅  ⋅  │  ⋅  ⋅  ⋅
 0  1  0  │  0  0  0  ⋅  │  ⋅  ⋅  ⋅
 ⋅  0  1  │  ⋅  0  0  0  │  ⋅  ⋅  ⋅
 ─────────┼──────────────┼─────────
 0  0  ⋅  │  1  0  ⋅  ⋅  │  0  0  ⋅
 0  0  0  │  0  1  0  ⋅  │  0  0  0
 ⋅  0  0  │  ⋅  0  1  0  │  ⋅  0  0
 ⋅  ⋅  0  │  ⋅  ⋅  0  1  │  ⋅  ⋅  0
 ─────────┼──────────────┼─────────
 ⋅  ⋅  ⋅  │  0  0  ⋅  ⋅  │  1  0  ⋅
 ⋅  ⋅  ⋅  │  0  0  0  ⋅  │  0  1  0
 ⋅  ⋅  ⋅  │  ⋅  0  0  0  │  ⋅  0  1

julia> BandedBlockBandedMatrix(Ones{Int}(10,13), [3,4,3], [4,5,4], (1,1), (1,1))
3×3-blocked 10×13 BandedBlockBandedMatrix{Int64} with block-bandwidths (1, 1) and sub-block-bandwidths block-bandwidths (1, 1):
 1  1  ⋅  ⋅  │  1  1  ⋅  ⋅  ⋅  │  ⋅  ⋅  ⋅  ⋅
 1  1  1  ⋅  │  1  1  1  ⋅  ⋅  │  ⋅  ⋅  ⋅  ⋅
 ⋅  1  1  1  │  ⋅  1  1  1  ⋅  │  ⋅  ⋅  ⋅  ⋅
 ────────────┼─────────────────┼────────────
 1  1  ⋅  ⋅  │  1  1  ⋅  ⋅  ⋅  │  1  1  ⋅  ⋅
 1  1  1  ⋅  │  1  1  1  ⋅  ⋅  │  1  1  1  ⋅
 ⋅  1  1  1  │  ⋅  1  1  1  ⋅  │  ⋅  1  1  1
 ⋅  ⋅  1  1  │  ⋅  ⋅  1  1  1  │  ⋅  ⋅  1  1
 ────────────┼─────────────────┼────────────
 ⋅  ⋅  ⋅  ⋅  │  1  1  ⋅  ⋅  ⋅  │  1  1  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  │  1  1  1  ⋅  ⋅  │  1  1  1  ⋅
 ⋅  ⋅  ⋅  ⋅  │  ⋅  1  1  1  ⋅  │  ⋅  1  1  1
```
