```
varest(x, method::NoiseEstimation; batch_size = 0, summary = mean)
```

信号 `x` のノイズ分散を指定された方法を使用して推定します

**入力**

  * `x`: 信号
  * `method`: ノイズ推定方法

      * `BayesianEst`: ベイズノイズ推定（実装予定）
      * `GCVEst`: 一般化交差検証（GCV）ノイズ推定
      * `LCurveEst`: L曲線ノイズ推定
      * `DerricoEst`: D'Erricoノイズ推定
  * `batch_size::Int`: バッチ処理のためのバッチサイズ（デフォルト = 0）
  * `summary`: バッチ処理のための要約関数（デフォルト = mean）
