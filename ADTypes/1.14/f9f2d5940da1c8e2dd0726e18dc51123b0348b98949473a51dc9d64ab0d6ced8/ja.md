```
column_coloring(M::AbstractMatrix, ca::ColoringAlgorithm)::AbstractVector{<:Integer}
```

アルゴリズム `ca` を使用して、`M` の列の構造的に直交する分割を構築します。

結果は、長さ `size(M, 2)` の色付けベクトル `c` であり、すべての非ゼロ係数 `M[i, j]` に対して、列 `j` は行 `i` において非ゼロ係数を持つその色 `c[j]` の唯一の列です。
