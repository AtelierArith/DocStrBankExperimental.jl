```
pmrand(::Type{PM}, n, m[, period = 2pi]; nh = 1) 
pmrand(::Type{PM{:c,T}}, n, m[, period = 2pi]; nh = 1) 
pmrand(n, m[, period = 2pi]; nh = 1) 
pmrand(PeriodicTimeSeriesMatrix, n, m[, period = 2pi]; ns = 1) 
pmrand(PeriodicTimeSeriesMatrix{:c,T}, n, m[, period = 2pi]; ns = 1) 
pmrand(PeriodicSwitchingMatrix, n, m[, period = 2pi]; ts = [0]) 
pmrand(PeriodicSwitchingMatrix{:c,T}, n, m[, period = 2pi]; ts = [0])
```

タイプ `PM` または `PM{:c,T}` のランダムな `n×m` 連続時間周期行列を生成し、周期 `period` を指定します（デフォルト: `period = 2pi`）。`PM` は生成される周期行列の結果のタイプを指定します。`PM = HarmonicArray`、または `PM = PeriodicFunctionMatrix`、または `PM = PeriodicSymbolicMatrix`、または `PM = FourierFunctionMatrix` の場合、結果の周期行列は `nh` 個の調和成分を持つランダムな調和表現に対応します（デフォルト: `nh = 1`）。行列要素のタイプ `T` は、例えば `HarmonicArray{:c,T}` を使用して指定でき、デフォルトでは `T = Float64` と仮定されます。`PM` が省略された場合、デフォルトで `PM = HarmonicArray` となります。

`PM = PeriodicTimeSeriesMatrix` の場合、`ns` はコンポーネント行列の数を指定します。

`PM = PeriodicSwitchingMatrix` の場合、ベクトル `ts` は切り替え時間を指定します。
