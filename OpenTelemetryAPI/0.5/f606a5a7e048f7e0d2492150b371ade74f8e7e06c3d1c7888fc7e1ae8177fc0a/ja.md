```
ObservableGauge{T}(callback, name, meter; unit = "", description = "",) where {T}
```

`ObservableGauge`は、観測されているときに非加算値（例：部屋の温度 - 複数の部屋からの温度値を報告して合計することは意味がありません）を報告する[`AbstractAsyncInstrument`](@ref)です。

詳細については、[仕様](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/metrics/api.md#asynchronous-gauge)を参照してください。
