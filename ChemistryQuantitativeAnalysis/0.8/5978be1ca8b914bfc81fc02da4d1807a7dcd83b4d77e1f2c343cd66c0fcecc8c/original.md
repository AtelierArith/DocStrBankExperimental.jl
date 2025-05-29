```
relative_signal(batch::Batch, at::AnalysisTable; signal = batch.method.signal)
relative_signal(method::AnalysisMethod, at::AnalysisTable; signal = method.signal)
relative_signal(batch::Batch, dt::AbstractDataTable)
relative_signal(method::AnalysisMethod, dt::AbstractDataTable)
```

Calculate relative signal using `getproperty(at, signal)` or `dt` as signal data, and return the result as `AbstractDataTable`.
