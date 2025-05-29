```
laplacian_spectrum(g[, T=Int; dir=:unspec])
```

グラフ `g` のラプラシアン行列の固有値を、頂点によってインデックス付けして返します。`T` のデフォルト値は [`laplacian_matrix`](@ref) のものと同じです。

### オプション引数

`dir=:unspec`: `dir` のオプションは [`laplacian_matrix`](@ref) のものと同じです。

### パフォーマンス

行列を密に変換し、$nv^2$ のメモリ使用量になります。

### 実装ノート

いくつかの固有値/固有ベクトルを計算するには `eigvals(Matrix(laplacian_matrix(g, args...)))` を使用します。
