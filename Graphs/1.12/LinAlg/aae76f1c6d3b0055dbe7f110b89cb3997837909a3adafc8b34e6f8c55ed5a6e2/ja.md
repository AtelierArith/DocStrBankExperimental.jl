```
adjacency_spectrum(g[, T=Int; dir=:unspec])
```

グラフ `g` の隣接行列の固有値を頂点でインデックス付けして返します。`T` のデフォルト値は [`adjacency_matrix`](@ref) と同じです。

### オプション引数

`dir=:unspec`: `dir` のオプションは [`laplacian_matrix`](@ref) と同じです。

### パフォーマンス

行列を密行列に変換し、$nv^2$ のメモリ使用量になります。

### 実装ノート

いくつかの固有値/固有ベクトルを計算するには `eigvals(Matrix(adjacency_matrix(g, args...)))` を使用します。
