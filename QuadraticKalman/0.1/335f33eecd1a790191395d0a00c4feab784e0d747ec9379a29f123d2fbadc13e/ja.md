```
kalman_smoother_truth_plot(X, results)
```

真の状態とカルマン平滑化推定値を比較するプロットを作成します。

# 引数

  * `X`: 真の状態値の行列 (N×T)
  * `results`: 平滑化された状態推定を含む SmootherOutput オブジェクト

# 戻り値

真の状態、平滑化された推定、および信頼区間を示すプロット
