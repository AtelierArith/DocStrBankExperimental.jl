```
EDF.SignalHeader
```

単一のEDF信号のヘッダーを表す型。

# フィールド

  * `label::String`: 信号のタイプ/センサーラベル、詳細は https://www.edfplus.info/specs/edftexts.html#label を参照
  * `transducer_type::String`: 非標準化されたトランスデューサタイプ情報
  * `physical_dimension::String`: 詳細は https://www.edfplus.info/specs/edftexts.html#physidim を参照
  * `physical_minimum::Float32`: 信号の物理的最小値
  * `physical_maximum::Float32`: 信号の物理的最大値
  * `digital_minimum::Float32`: データレコード内で発生する可能性のある信号の最小値
  * `digital_maximum::Float32`: データレコード内で発生する可能性のある信号の最大値
  * `prefilter::String`: 非標準化されたプレフィルタリング情報
  * `samples_per_record::Int32`: データレコード内のサンプル数（全体ではなく）
