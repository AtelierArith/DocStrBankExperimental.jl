```
View(name=nothing;kwargs...)
```

`name`はワイルドカードをサポートしています。

詳細は[仕様](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/metrics/sdk.md#view)を参照してください。

## キーワード引数

  * `description = nothing`,
  * `attribute_keys = nothing`,
  * `extra_dimensions = BoundedAttributes()`,
  * `aggregation = nothing`,
  * `instrument_name = nothing`,
  * `instrument_type = nothing`,
  * `meter_name = nothing`,
  * `meter_version = nothing`,
  * `meter_schema_url = nothing`,
