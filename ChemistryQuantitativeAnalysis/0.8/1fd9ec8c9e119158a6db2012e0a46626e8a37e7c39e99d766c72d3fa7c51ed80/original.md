```
update_quantification!(batch::Batch; signal = batch.method.signal, rel_sig = batch.method.rel_sig, est_conc = batch.method.est_conc)
```

Quantify all analytes using `getproperty(at, signal)` as signal data, update or insert the values into `batch.data` at index `rel_sig` for relative signal and `est_conc` for concentration, and returns the updated `batch`.
