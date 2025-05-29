```
ObservableGauge{T}(callback, name, meter; unit = "", description = "",) where {T}
```

`ObservableGauge` is an [`AbstractAsyncInstrument`](@ref) which reports non-additive value(s) (e.g. the room temperature - it makes no sense to report the temperature value from multiple rooms and sum them up) when the instrument is being observed.

See also the details from [the specification](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/metrics/api.md#asynchronous-gauge)
