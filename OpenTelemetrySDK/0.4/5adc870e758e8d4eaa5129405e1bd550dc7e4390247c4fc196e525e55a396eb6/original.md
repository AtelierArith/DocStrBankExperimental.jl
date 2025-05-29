```
OtelBatchLogger(exporter;kw...)
```

`OtelBatchLogger` is a `Sink` (see [LoggingExtras.jl](https://github.com/JuliaLogging/LoggingExtras.jl) to understand the concept).  Note that it will create a [`OtelLogTransformer`](@ref) on construction and apply it automatically on each log message.

# Keyword arguments

  * `max_queue_size=nothing`
  * `scheduled_delay_millis = nothing`
  * `export_timeout_millis = nothing`
  * `max_export_batch_size = nothing`
  * `resource = Resource()`
  * `instrumentation_scope = InstrumentationScope()`
