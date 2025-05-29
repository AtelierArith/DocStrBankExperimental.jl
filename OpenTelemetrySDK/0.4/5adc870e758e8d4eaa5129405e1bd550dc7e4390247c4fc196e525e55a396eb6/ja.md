```
OtelBatchLogger(exporter;kw...)
```

`OtelBatchLogger` は `Sink` です（この概念を理解するには [LoggingExtras.jl](https://github.com/JuliaLogging/LoggingExtras.jl) を参照してください）。これは、構築時に [`OtelLogTransformer`](@ref) を作成し、各ログメッセージに自動的に適用することに注意してください。

# キーワード引数

  * `max_queue_size=nothing`
  * `scheduled_delay_millis = nothing`
  * `export_timeout_millis = nothing`
  * `max_export_batch_size = nothing`
  * `resource = Resource()`
  * `instrumentation_scope = InstrumentationScope()`
