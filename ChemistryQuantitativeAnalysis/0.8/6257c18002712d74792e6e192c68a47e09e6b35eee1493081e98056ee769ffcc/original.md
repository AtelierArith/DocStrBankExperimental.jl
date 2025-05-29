```
update_accuracy!(batch::Batch; true_conc = batch.method.true_conc, est_conc = batch.method.est_conc, acc = batch.method.acc)
```

Calculate accuracy, and update or insert the values into `batch.data` or a copy of `batch.data` at index `acc`, and returns the updated `batch`. Use `getproperty(batch.data, true_conc)` as true concentration and `getproperty(batch.data, est_conc)` as estimated concentration.  This function assigns `at` to `batch.data` 
