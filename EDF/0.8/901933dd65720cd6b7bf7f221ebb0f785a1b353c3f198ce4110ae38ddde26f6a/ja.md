```
EDF.FileHeader
```

`EDF.File`の解析されたヘッダーレコードを表す型（信号ヘッダーを除く）。

# フィールド

  * `version::String`: データフォーマットのバージョン
  * `patient::Union{String,PatientID}`: ローカル患者識別
  * `recording::Union{String,RecordingID}`: ローカル録音識別
  * `start::DateTime`: 録音の開始日時
  * `is_contiguous::Bool`: `true`の場合、データレコードは連続している; EDF+準拠でないファイルの場合は`true`
  * `record_count::Int`: 録音内のデータレコードの数
  * `seconds_per_record::Float64`: データレコードの持続時間（秒）
