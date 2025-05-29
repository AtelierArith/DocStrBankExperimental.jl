```
IEKFMeasurementModel{IPM}(measurement, R2, ny, Cjac, cache = nothing)
```

反復拡張カルマンフィルタのための測定モデル。

# 引数:

  * `IPM`: 測定関数がインプレースであるかどうかを示すブール値
  * `measurement`: 測定関数 `y = h(x, u, p, t)`
  * `R2`: 測定ノイズ共分散行列
  * `ny`: 測定変数の数
  * `Cjac`: 測定関数のヤコビアン `Cjac(x, u, p, t)`。提供されない場合は、ForwardDiffが使用されます。
  * `step`: ガウス-ニュートン法におけるステップサイズ。0と1の間のFloat64である必要があります。
  * `maxiters`: IEKF内のガウス-ニュートン法の最大反復回数
  * `epsilon`: IEKF内のガウス-ニュートン法の収束基準
  * `cache`: ヤコビアンのキャッシュ
