```
set_relative_signal(at::AbstractDataTable, batch::Batch; signal = batch.method.signal, rel_sig = batch.method.rel_sig)
set_relative_signal(at::AnalysisTable, method::AnalysisMethod; signal = method.signal, rel_sig = method.rel_sig)
```

`getproperty(at, signal)`を信号データとして使用して相対信号を計算し、`rel_sig`のインデックスで`at`のコピーに値を更新または挿入し、そのコピーを返します。
