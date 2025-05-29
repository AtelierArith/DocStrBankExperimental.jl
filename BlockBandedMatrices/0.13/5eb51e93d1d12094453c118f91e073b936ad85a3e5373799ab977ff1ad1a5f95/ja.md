```
BlockBandedMatrix(A::Union{AbstractMatrix,UniformScaling},
                    rows::AbstractVector{Int}, cols::AbstractVector{Int},
                    (l,u)::NTuple{2,Int})
```

`rows` と `cols` のブロックを持つ `sum(rows) × sum(cols)` の `BlockBandedMatrix` を返します。ブロックバンド幅は `(l,u)` です。構造的な非ゼロエントリは `A` の対応するインデックスに等しくなります。

# 例

```jldoctest
julia> using LinearAlgebra, FillArrays

julia> l,u = 0,1; # ブロックバンド幅

julia> nrowblk, ncolblk = 3, 3; # 行/列ブロックの数

julia> rows = 1:nrowblk; cols = 1:ncolblk; # ブロックサイズ

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
