```
freqtab(X, V;intervalX = 1.0, intervalV = 1.0, scaleX = minimum(X):intervalX:maximum(X), scaleV = minimum(V):intervalV:maximum(V))
```

`NEATFreqTab`をNEATデザインのために作成します。

# 引数

  * `X` 対象テストの生スコアのベクトル（欠損値を除く）。
  * `V` アンカーテストの生スコアのベクトル（欠損値を除く）。
