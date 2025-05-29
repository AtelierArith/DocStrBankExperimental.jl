```
relative_signal(batch::Batch, at::AnalysisTable; signal = batch.method.signal)
relative_signal(method::AnalysisMethod, at::AnalysisTable; signal = method.signal)
relative_signal(batch::Batch, dt::AbstractDataTable)
relative_signal(method::AnalysisMethod, dt::AbstractDataTable)
```

`getproperty(at, signal)` または `dt` を信号データとして使用して相対信号を計算し、結果を `AbstractDataTable` として返します。
