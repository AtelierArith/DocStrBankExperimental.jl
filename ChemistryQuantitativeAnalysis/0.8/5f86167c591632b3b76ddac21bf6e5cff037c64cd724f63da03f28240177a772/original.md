```
inv_predict(batch::Batch, at::AnalysisTable; rel_sig = batch.method.rel_sig)
inv_predict(batch::Batch, dt::AbstractDataTable)
```

Inversely predict concentration based on relative signal data, `getproperty(at, rel_sig)` or `dt`, and return the result as `AbstractDataTable`.
