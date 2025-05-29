```
update_quantification!(batch::Batch; signal = batch.method.signal, rel_sig = batch.method.rel_sig, est_conc = batch.method.est_conc)
```

すべての分析物を `getproperty(at, signal)` を信号データとして定量化し、相対信号のために `rel_sig` で、濃度のために `est_conc` で `batch.data` に値を更新または挿入し、更新された `batch` を返します。
