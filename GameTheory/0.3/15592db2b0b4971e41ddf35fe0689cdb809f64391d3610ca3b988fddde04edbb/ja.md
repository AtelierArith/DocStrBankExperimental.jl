```
LocalInteraction(g, adj_matrix[, revision=SimultaneousRevision()])
```

`LocalInteraction` インスタンスを構築します。

# 引数

  * `g::NormalFormGame` : モデルで使用されるゲーム。
  * `adj_matrix::AbstractMatrix` : モデル内のグラフの隣接行列。
  * `revision::AbstractRevision` : 改訂方法を指定する引数； `SimultaneousRevision()` または `AsynchronousRevision()`。

# 戻り値

  * `::LocalInteraction` : ローカルインタラクションモデル。
