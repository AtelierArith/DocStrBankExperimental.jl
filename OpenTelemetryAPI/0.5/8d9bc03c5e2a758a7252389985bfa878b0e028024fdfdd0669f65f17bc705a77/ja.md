```
ObservableCounter{T}(callback, name, meter; unit = "", description = "") where {T}
```

`ObservableCounter`は、観測されているときに単調増加する値を報告する[`AbstractAsyncInstrument`](@ref)です。

詳細は[仕様](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/metrics/api.md#asynchronous-counter)を参照してください。
