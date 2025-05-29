```
pdf(covar::ForwardCovariance, coordinates::Dict{Symbol,Real})
```

指定した座標でのpdfの値を取得します。多変量ガウス分布の平均がゼロベクトルであると仮定されています。

### 入力

  * `covar` - pdfを評価したい`ForwardCovariance`構造体
  * `coordinates` - 検査したい座標。

### 出力

  * スカラー
