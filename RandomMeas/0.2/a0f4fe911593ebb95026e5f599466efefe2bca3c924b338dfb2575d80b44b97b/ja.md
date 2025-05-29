```
get_XEB(ψ::MPS, measurement_data::MeasurementData)
```

`measurement_data`の測定結果に対する線形交差エントロピーを、理論状態`ψ`に対して返します。

# 引数:

  * `ψ::MPS`: 比較対象となる理論状態。
  * `measurement_data::MeasurementData`: 結果と設定を含む測定データオブジェクト。

# 戻り値:

`Float64`としての線形交差エントロピー。
