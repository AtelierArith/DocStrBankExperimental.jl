```
log_likelihood(covar::ForwardCovariance, coordinates::Dict{Symbol,Real})
```

指定された座標で対数尤度を取得します。多変量ガウス分布の平均がゼロベクトルであると仮定されています。

### 入力

  * `covar` - 対数尤度を評価したい `ForwardCovariance` 構造体。
  * `coordinates` - 検査したい座標。

### 出力

  * スカラー
