```
denoising(y::AbstractArray, alg)
```

信号 `y` のノイズ除去を行います。

**入力**

  * `y`: ノイズのある信号
  * `alg`: ノイズ除去方法

      * `BayesDenoising`: ベイズ正則化ノイズ除去法（実装予定）
      * `GCVDenoising`: GCVノイズ除去法
      * `LCurveDenoising`: L-カーブノイズ除去法
      * `KalmanDenoising`: カルマンフィルターノイズ除去法

**出力**

  * `x`: ノイズ除去された信号
