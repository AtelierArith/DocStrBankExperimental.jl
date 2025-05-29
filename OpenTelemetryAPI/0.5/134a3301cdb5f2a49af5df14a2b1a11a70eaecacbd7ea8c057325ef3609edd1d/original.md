```
ObservableUpDownCounter{T}(callback, name, meter; unit = "", description = "") where {T}
```

`ObservableUpDownCounter` is an [`AbstractAsyncInstrument`](@ref) which reports additive value(s) (e.g. the process heap size - it makes sense to report the heap size from multiple processes and sum them up, so we get the total heap usage) when the instrument is being observed.

See more details from [the specification](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/metrics/api.md#asynchronous-updowncounter).
