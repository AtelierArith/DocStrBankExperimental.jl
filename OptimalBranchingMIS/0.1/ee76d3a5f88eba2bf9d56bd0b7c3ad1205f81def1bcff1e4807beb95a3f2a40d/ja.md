```
counting_mis1(g::SimpleGraph)
```

与えられた `SimpleGraph` の最大独立集合 (MIS) を計算するために、まずそれを `EliminateGraph` に変換し、その後 `counting_mis1` 関数を適用します。

# 引数

  * `g::SimpleGraph`: 最大独立集合を計算するための入力グラフ。

# 戻り値

  * `MISCount`: 提供されたグラフの最大独立集合のサイズと分岐のカウント。
