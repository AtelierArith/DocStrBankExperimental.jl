```
set_relative_signal!(at::AnalysisTable, batch::Batch; signal = batch.method.signal, rel_sig = batch.method.rel_sig)
set_relative_signal!(at::AnalysisTable, method::AnalysisMethod; signal = method.signal, rel_sig = method.rel_sig)
```

`getproperty(at, signal)`を信号データとして使用して相対信号を計算し、値を`at`のインデックス`rel_sig`に更新して挿入し、`at`を返します。
