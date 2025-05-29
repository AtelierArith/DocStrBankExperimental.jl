```
set_quantification(at::AnalysisTable, batch::Batch; signal = batch.method.signal, rel_sig = batch.method.rel_sig, est_conc = batch.method.est_conc)
```

すべての分析物を `getproperty(at, signal)` を信号データとして定量化し、相対信号のためのインデックス `rel_sig` と濃度のための `est_conc` に `at` のコピーに値を更新または挿入し、そのコピーを返します。
