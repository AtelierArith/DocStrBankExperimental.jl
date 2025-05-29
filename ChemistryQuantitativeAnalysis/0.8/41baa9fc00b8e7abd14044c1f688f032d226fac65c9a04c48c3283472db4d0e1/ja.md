```
quantification(batch::Batch, at::AnalysisTable; signal = batch.method.signal)
quantification(batch::Batch, dt::AbstractDataTable)
```

相対信号データに基づいてすべての分析を定量化し、`getproperty(at, signal)`または`dt`を信号データとして使用して結果を`AbstractDataTable`として返します。
