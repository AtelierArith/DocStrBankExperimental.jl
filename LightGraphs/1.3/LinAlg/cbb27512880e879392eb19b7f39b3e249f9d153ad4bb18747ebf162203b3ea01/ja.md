```
laplacian_matrix(g[, T=Int; dir=:unspec])
```

グラフ `g` のスパース [ラプラシアン行列](https://en.wikipedia.org/wiki/Laplacian_matrix) を返します。インデックスは `[u, v]` 頂点です。`T` は両方のグラフタイプに対して `Int` にデフォルト設定されています。

### オプション引数

`dir=:unspec`: `:unspec`、`:both`、`:in`、および `:out` が現在サポートされています。無向グラフの場合、`dir` はデフォルトで `:out` になります。向き付きグラフの場合、`dir` はデフォルトで `:both` になります。
