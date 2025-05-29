```
ObservableUpDownCounter{T}(callback, name, meter; unit = "", description = "") where {T}
```

`ObservableUpDownCounter` は [`AbstractAsyncInstrument`](@ref) であり、観測されているときに加算値（例えば、プロセスのヒープサイズ - 複数のプロセスからヒープサイズを報告し、それらを合計することが意味を持つため、合計ヒープ使用量を得ることができます）を報告します。

詳細については [仕様](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/metrics/api.md#asynchronous-updowncounter) を参照してください。
