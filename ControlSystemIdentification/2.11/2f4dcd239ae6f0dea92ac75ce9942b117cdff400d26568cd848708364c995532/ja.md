```
model, x0 = subspaceid(frd::FRD, Ts, args...; estimate_x0 = false, bilinear_transform = false, kwargs...)
```

周波数応答データオブジェクトが提供されると

  * FRDは自動的に[`InputOutputFreqData`](@ref)に変換されます。
  * `estimate_x0`はデフォルトで0に設定されます。
  * `bilinear_transform`は周波数ベクトルを離散時間に変換します。以下の注意を参照してください。

注意: 周波数応答データが周波数応答分析から得られた場合、推定の前にデータの双線形変換が必要です。この変換は`bilinear_transform = true`の場合に適用されます。
