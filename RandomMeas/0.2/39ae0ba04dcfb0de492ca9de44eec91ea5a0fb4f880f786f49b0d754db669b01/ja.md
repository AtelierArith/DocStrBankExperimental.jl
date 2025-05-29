```
get_overlap(
    data_1::MeasurementData,
    data_2::MeasurementData
)
```

2つの量子状態の重なりを単一の測定設定で計算します。

# 引数

  * `data_1::MeasurementData`: 最初の状態の測定データ、次元は `(NM, N)`。
  * `data_2::MeasurementData`: 2番目の状態の測定データ、次元は `(NM, N)`。

# 戻り値

  * 単一の測定設定に対して計算された重なり。
