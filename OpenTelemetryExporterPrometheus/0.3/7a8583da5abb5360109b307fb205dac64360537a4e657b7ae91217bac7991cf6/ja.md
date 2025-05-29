```
PrometheusExporter(; kw...)
```

## キーワード引数

  * `host`、デフォルト値は `OTEL_EXPORTER_PROMETHEUS_HOST` 環境変数から読み取られます。
  * `port`、デフォルト値は `OTEL_EXPORTER_PROMETHEUS_PORT` 環境変数から読み取られます。
  * `resource_to_telemetry_conversion=false`、有効にすると、すべてのリソース属性がデフォルトでメトリックラベルに変換されます。
  * `path="/metrics"`、デフォルトのURLパス。

## 使用法

```julia
r = MetricReader(PrometheusExporter())
```

`PrometheusExporter` はプルベースのエクスポーターであることに注意してください。メトリックを更新するために `r()` を実行する必要はありません。
