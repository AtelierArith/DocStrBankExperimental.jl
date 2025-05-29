```
laplacian_matrix(g[, T=Int; dir=:unspec])
```

グラフ `g` のスパース [ラプラシアン行列](https://en.wikipedia.org/wiki/Laplacian_matrix) を返します。インデックスは `[u, v]` の頂点です。`T` は両方のグラフタイプに対してデフォルトで `Int` です。

### オプション引数

`dir=:unspec`: 現在サポートされているのは `:unspec`、 `:both`、 `:in`、および `:out` です。無向グラフの場合、`dir` はデフォルトで `:out` です。有向グラフの場合、`dir` はデフォルトで `:both` です。
