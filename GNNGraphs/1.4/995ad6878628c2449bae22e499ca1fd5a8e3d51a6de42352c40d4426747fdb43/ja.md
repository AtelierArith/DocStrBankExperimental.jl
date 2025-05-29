```
normalized_laplacian(g, T=Float32; add_self_loops=false, dir=:out)
```

グラフ `g` の正規化ラプラシアン行列。

# 引数

  * `g`: `GNNGraph`。
  * `T`: 結果の要素型。
  * `add_self_loops`: 行列を計算する際に自己ループを追加する。
  * `dir`: 考慮されるエッジの方向性 (:out, :in, :both)。
