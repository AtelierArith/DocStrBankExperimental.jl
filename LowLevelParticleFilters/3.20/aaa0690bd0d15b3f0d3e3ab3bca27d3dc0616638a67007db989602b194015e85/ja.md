```
EKFMeasurementModel{IPM}(measurement, R2, ny, Cjac, cache = nothing)
```

拡張カルマンフィルタのための測定モデル。

# 引数:

  * `IPM`: 測定関数がインプレースであるかどうかを示すブール値
  * `measurement`: 測定関数 `y = h(x, u, p, t)`
  * `R2`: 測定ノイズ共分散行列
  * `ny`: 測定変数の数
  * `Cjac`: 測定関数のヤコビアン `Cjac(x, u, p, t)`。提供されない場合は、ForwardDiffが使用されます。
