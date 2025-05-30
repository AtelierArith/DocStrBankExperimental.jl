```
symmetric_coloring(M::AbstractMatrix, ca::ColoringAlgorithm)::AbstractVector{<:Integer}
```

アルゴリズム `ca` を使用して、対称行列 `M` の列（または行）の対称的に構造的に直交する分割を構築します。

結果は、長さ `size(M, 1) == size(M, 2)` の彩色ベクトル `c` であり、非ゼロ係数 `M[i, j]` に対して、次の条件のいずれかが成り立ちます：

  * 列 `j` は、行 `i` において非ゼロ係数を持つその色 `c[j]` の唯一の列である；
  * 列 `i` は、行 `j` において非ゼロ係数を持つその色 `c[i]` の唯一の列である。
