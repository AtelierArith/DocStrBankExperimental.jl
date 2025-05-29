```
Exemplar(;kw...)
```

Exemplarは集約データの例データポイントです。トレースとメトリックとの関係を理解するために[仕様](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/metrics/sdk.md#exemplar)を読んでください。

## キーワード引数:

  * `value`
  * `time_unix_nano`
  * `filtered_attributes`、[`Measurement`](@ref)の追加属性で、[`Metric`](@ref)の`:attribute_keys`フィールドには含まれていません。
  * `trace_id`、測定が行われるときのスパンコンテキスト内の`trace_id`。
  * `span_id`、測定が行われるときのスパンコンテキスト内の`span_id`。
