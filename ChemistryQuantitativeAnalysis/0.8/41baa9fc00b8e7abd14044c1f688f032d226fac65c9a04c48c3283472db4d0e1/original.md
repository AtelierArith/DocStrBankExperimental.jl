```
quantification(batch::Batch, at::AnalysisTable; signal = batch.method.signal)
quantification(batch::Batch, dt::AbstractDataTable)
```

Quantify all analyes based on relative signal data, and return the result as `AbstractDataTable` using `getproperty(at, signal)` or `dt` as signal data.
