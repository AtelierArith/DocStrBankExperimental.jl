```
BlockSkylineMatrix{T,LL,UU}(M::Union{UndefInitializer,UniformScaling,AbstractMatrix},
                            rows, cols, (l::LL, u::UU))
```

returns a `sum(rows)`×`sum(cols)` block-banded matrix `A` having elements of type `T`, with block-bandwidths `(l,u)`, and where `A[Block(K,J)]` is a `Matrix{T}` of size `rows[K]`×`cols[J]`.

`(l,u)` may be integers for constant bandwidths, or integer vectors of length `length(cols)` for ragged bands. In the latter case, `l` and `u` represent the number of sub and super-block-bands in each column.

# Examples

```jldoctest
julia> using LinearAlgebra, FillArrays

julia> BlockSkylineMatrix(I, [2,2,2,4], [1,2,3], ([2,0,1],[0,1,1]))
4×3-blocked 10×6 BlockSkylineMatrix{Bool, Vector{Bool}, BlockBandedMatrices.BlockSkylineSizes{Tuple{BlockArrays.BlockedOneTo{Int64, Vector{Int64}}, BlockArrays.BlockedOneTo{Int64, Vector{Int64}}}, Vector{Int64}, Vector{Int64}, BandedMatrices.BandedMatrix{Int64, Matrix{Int64}, Base.OneTo{Int64}}, Vector{Int64}}}:
 1  │  0  0  │  ⋅  ⋅  ⋅
 0  │  1  0  │  ⋅  ⋅  ⋅
 ───┼────────┼─────────
 0  │  0  1  │  0  0  0
 0  │  0  0  │  1  0  0
 ───┼────────┼─────────
 0  │  ⋅  ⋅  │  0  1  0
 0  │  ⋅  ⋅  │  0  0  1
 ───┼────────┼─────────
 ⋅  │  ⋅  ⋅  │  0  0  0
 ⋅  │  ⋅  ⋅  │  0  0  0
 ⋅  │  ⋅  ⋅  │  0  0  0
 ⋅  │  ⋅  ⋅  │  0  0  0

julia> BlockSkylineMatrix(Ones(9,6), [2,3,4], [1,2,3], ([2,0,0],[0,1,1]))
3×3-blocked 9×6 BlockSkylineMatrix{Float64, Vector{Float64}, BlockBandedMatrices.BlockSkylineSizes{Tuple{BlockArrays.BlockedOneTo{Int64, Vector{Int64}}, BlockArrays.BlockedOneTo{Int64, Vector{Int64}}}, Vector{Int64}, Vector{Int64}, BandedMatrices.BandedMatrix{Int64, Matrix{Int64}, Base.OneTo{Int64}}, Vector{Int64}}}:
 1.0  │  1.0  1.0  │   ⋅    ⋅    ⋅
 1.0  │  1.0  1.0  │   ⋅    ⋅    ⋅
 ─────┼────────────┼───────────────
 1.0  │  1.0  1.0  │  1.0  1.0  1.0
 1.0  │  1.0  1.0  │  1.0  1.0  1.0
 1.0  │  1.0  1.0  │  1.0  1.0  1.0
 ─────┼────────────┼───────────────
 1.0  │   ⋅    ⋅   │  1.0  1.0  1.0
 1.0  │   ⋅    ⋅   │  1.0  1.0  1.0
 1.0  │   ⋅    ⋅   │  1.0  1.0  1.0
 1.0  │   ⋅    ⋅   │  1.0  1.0  1.0
```
