```
ObservableCounter{T}(callback, name, meter; unit = "", description = "") where {T}
```

`ObservableCounter` is an [`AbstractAsyncInstrument`](@ref) which reports monotonically increasing value(s) when the instrument is being observed.

See more details from [the specification](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/metrics/api.md#asynchronous-counter)
