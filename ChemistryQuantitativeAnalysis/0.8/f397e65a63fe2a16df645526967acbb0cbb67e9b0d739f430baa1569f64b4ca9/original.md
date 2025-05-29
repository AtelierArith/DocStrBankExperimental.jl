```
update_inv_predict!(batch::Batch; rel_sig = batch.method.rel_sig, est_conc = batch.method.est_conc)
```

Inversely predict concentration using `getproperty(batch.data, rel_sig)` or `dt` as relstive signal data, update or insert the value into `batch.data` at index `est_conc` and returns the updated `batch`.
