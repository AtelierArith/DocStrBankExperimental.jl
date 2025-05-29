```
AffineParametricArray{T, N, MT<:AbstractArray{T, N}}
```

要素がパラメータのセット $p₁, p₂, …, pₙ$ に対してアフィン依存性を持つ配列。

### フィールド

  * coeffs::Vector{MT} – 各変数の係数に対応する配列のベクトル。

### 例

```jldoctest
julia> @affinevars x y z
3-element Vector{AffineExpression{Int64}}:
 x
 y
 z

julia> A = AffineParametricArray([x+y x-1;x+y+z 1])
2×2 AffineParametricMatrix{Int64, Matrix{Int64}}:
 x+y    x-1
 x+y+z  1
```
