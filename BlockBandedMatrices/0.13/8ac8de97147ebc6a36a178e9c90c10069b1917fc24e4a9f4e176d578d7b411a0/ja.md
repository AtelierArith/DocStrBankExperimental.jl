```
BlockBandedMatrix(A::AbstractMatrix, (l,u)::NTuple{2,Int})
```

ブロックバンド幅 `(l,u)` を持つ `BlockBandedMatrix` を返します。ここで、構造的な非ゼロブロックは `A` のそれに対応します。

例

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
