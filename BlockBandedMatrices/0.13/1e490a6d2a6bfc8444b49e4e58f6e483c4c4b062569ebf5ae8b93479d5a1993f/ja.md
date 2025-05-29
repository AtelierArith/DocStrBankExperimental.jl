```
BandedBlockBandedMatrix(M::Union{UniformScaling,AbstractMatrix},
                           rows, cols, (l, u), (λ, μ))
```

`sum(rows) × sum(cols)` のバンドブロックバンド行列 `A` を返します。ブロックバンド幅は `(l,u)` であり、`A[Block(K,J)]` はサイズ `rows[K]`×`cols[J]` の `BandedMatrix` で、バンド幅は `(λ,μ)` です。返される行列の構造的な非ゼロ要素は、`M` のそれに対応します。

# 例

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
