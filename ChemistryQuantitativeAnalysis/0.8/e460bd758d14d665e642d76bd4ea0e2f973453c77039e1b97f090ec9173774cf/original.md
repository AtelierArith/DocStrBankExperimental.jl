```
set_quantification!(at::AnalysisTable, batch::Batch; signal = batch.method.signal, rel_sig = batch.method.rel_sig, est_conc = batch.method.est_conc)
```

Quantify all analytes, update or insert the values into `at` at index `rel_sig` for relative signal and `est_conc` for concentration, and return `at`.
