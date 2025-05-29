```
set_relative_signal!(at::AnalysisTable, batch::Batch; signal = batch.method.signal, rel_sig = batch.method.rel_sig)
set_relative_signal!(at::AnalysisTable, method::AnalysisMethod; signal = method.signal, rel_sig = method.rel_sig)
```

Calculate relative signal using `getproperty(at, signal)` as signal data, update and insert the value into `at` at index `rel_sig`, and return `at`.
