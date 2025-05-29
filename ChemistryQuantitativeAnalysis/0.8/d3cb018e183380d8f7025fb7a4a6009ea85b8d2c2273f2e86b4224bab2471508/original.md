```
set_accuracy(at::AnalysisTable, method::AnalysisMethod; true_conc = method.true_conc, est_conc = method.est_conc, acc = method.acc)
set_accuracy(at::AnalysisTable, batch::Batch; true_conc = batch.method.true_conc, est_conc = batch.method.est_conc, acc = batch.method.acc)
```

Calculate accuracy, update or insert the values into a copy of `at` at index `acc`, and return the copy.  using `getproperty(at, true_conc)` as true concentration and `getproperty(at, est_conc)` as estimated concentration.
