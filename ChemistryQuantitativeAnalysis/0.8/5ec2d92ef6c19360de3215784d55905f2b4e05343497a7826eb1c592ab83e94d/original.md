```
set_inv_predict!(at::AnalysisTable, batch::Batch; rel_sig = batch.method.rel_sig, est_conc = batch.method.est_conc)
```

Inversely predict concantration using `getproperty(at, rel_sig)` as relstive signal data, update or insert the value into `at` at index `est_conc`, and return `at`.
