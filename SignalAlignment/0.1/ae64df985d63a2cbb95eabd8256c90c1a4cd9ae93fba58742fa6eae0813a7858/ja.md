```
align_signals(signals, method; master = Index(1), by = nothing, output = Indices())
```

ベクトル `signals` 内のすべての信号を整列させます。

# 引数:

  * `signals`: 信号のベクトル
  * `method`: `Delay, XcorrDelay, DTWDelay, Warp` のいずれか
  * `master`: 他のすべてを整列させる信号、例: `Index(1), Longest(), Shortest(), Centroid(), Barycenter()`
  * `by`: 整列前に信号に適用されるオプションの関数
  * `output`: `Indices()` または `Signals()`。デフォルトは信号を整列させるインデックスを出力します。`output = Signals()` の場合、整列が適用され、整列された信号が返されます。
