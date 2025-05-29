```
LjungBoxTest(y, lag, dof=0)
```

時系列 `y` の独立性の帰無仮説を検定するために、Ljung-Box `Q` 統計量を計算します。

`lag` は `Q` の構築に使用されるラグの数を指定します。推定モデルの残差を検定する場合、`dof` は推定されたパラメータの数に設定する必要があります。例えば、ARIMA(p,0,q) モデルの残差を検定する場合、`dof=p+q` に設定します。

# 外部リンク

  * [Ljung-Box test on Wikipedia](https://en.wikipedia.org/wiki/Ljung–Box_test)
