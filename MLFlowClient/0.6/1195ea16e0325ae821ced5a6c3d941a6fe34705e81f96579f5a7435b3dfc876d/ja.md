```
Metric <: LoggingData
```

実行に関連付けられたメトリックで、キーと値のペアとして表されます。

# フィールド

  * `key::String`: このメトリックを識別するキー。
  * `value::Float64`: このメトリックに関連付けられた値。
  * `timestamp::Int64`: このメトリックが記録されたタイムスタンプ。
  * `step::Union{Int64, Nothing}`: メトリックをログするステップ。
