```
laplacian_lambda_max(g::GNNGraph, T=Float32; add_self_loops=false, dir=:out)
```

グラフ `g` の正規化対称ラプラシアンの最大固有値を返します。

グラフが複数のグラフからバッチ処理されている場合は、各グラフの最大固有値のリストを返します。
