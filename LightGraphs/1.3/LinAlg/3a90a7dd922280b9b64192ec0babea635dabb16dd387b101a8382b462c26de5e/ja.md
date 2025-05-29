```
laplacian_spectrum(g[, T=Int; dir=:unspec])
```

グラフ `g` のラプラシアン行列の固有値を頂点でインデックス付けして返します。`T` のデフォルト値は [`laplacian_matrix`](@ref) と同じです。

### オプション引数

`dir=:unspec`: `dir` のオプションは [`laplacian_matrix`](@ref) と同じです。

### パフォーマンス

行列を密行列に変換し、$nv^2$ のメモリ使用量になります。

### 実装ノート

固有値/固有ベクトルの一部を計算するには `eigs(laplacian_matrix(g);  kwargs...)` を使用します。
