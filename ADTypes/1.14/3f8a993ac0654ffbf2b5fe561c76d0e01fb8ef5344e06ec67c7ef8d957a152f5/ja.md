```
row_coloring(M::AbstractMatrix, ca::ColoringAlgorithm)::AbstractVector{<:Integer}
```

アルゴリズム `ca` を使用して、`M` の行の構造的に直交する分割を構築します。

結果は、長さ `size(M, 1)` の彩色ベクトル `c` であり、すべての非ゼロ係数 `M[i, j]` に対して、行 `i` は列 `j` に非ゼロ係数を持つその色 `c[i]` の唯一の行です。
