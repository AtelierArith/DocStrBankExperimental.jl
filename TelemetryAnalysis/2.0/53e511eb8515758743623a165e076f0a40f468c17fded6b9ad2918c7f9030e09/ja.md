```
struct TelemetryDatabase{F1 <: Function, F2 <: Function}
```

テレメトリデータベースを定義します。

# フィールド

  * `label::String`: データベースのラベル。
  * `get_telemetry_timestamp::F1`: テレメトリパケットのタイムスタンプを取得するための関数。
  * `unpack_telemetry::F2`: テレメトリパケットを展開し、転送関数に渡されるデータを取得するための関数。
  * `variables::OrderedDict{Symbol, TelemetryVariableDescription}`: テレメトリ変数。
