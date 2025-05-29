```
minrank_completion(A::SparseMatrixCSC{Tv, Ti}) where {Tv <: AbstractFloat, Ti <: Integer}
```

与えられたコーダルスパース行列 `A` の最小ランク補完 (`A_complete = Y*Yᵀ`) のコレスキー因子を返します。これは [Sun15] のアルゴリズム2を使用しています。このアルゴリズムは `A` のスーパーノード消去木を使用し、したがって BLAS レベル 3 の操作を行います。

# 参考文献

[Sun15] [半正定値最適化のための分解法 (博士論文)](https://escholarship.org/content/qt1cv6981p/qt1cv6981p.pdf) 著者: Yifan Sun
