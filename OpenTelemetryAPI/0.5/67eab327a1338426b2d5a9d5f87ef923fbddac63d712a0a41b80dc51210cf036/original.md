```
Histogram{T}(name, meter; unit = "", description = "") where {T}
```

`Histogram` is an `AbstractSyncInstrument` which can be used to report arbitrary values that are likely to be statistically meaningful. It is intended for statistics such as histograms, summaries, and percentile.

See more details from [the specification](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/metrics/api.md#histogram)
