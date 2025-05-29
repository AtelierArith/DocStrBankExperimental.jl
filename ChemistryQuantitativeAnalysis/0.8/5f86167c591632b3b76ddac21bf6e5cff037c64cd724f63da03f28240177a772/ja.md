```
inv_predict(batch::Batch, at::AnalysisTable; rel_sig = batch.method.rel_sig)
inv_predict(batch::Batch, dt::AbstractDataTable)
```

相対信号データ `getproperty(at, rel_sig)` または `dt` に基づいて濃度を逆に予測し、結果を `AbstractDataTable` として返します。
