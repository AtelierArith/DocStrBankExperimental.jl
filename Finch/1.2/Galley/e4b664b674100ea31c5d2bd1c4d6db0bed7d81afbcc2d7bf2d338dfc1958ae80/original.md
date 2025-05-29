```
galley_scheduler(verbose = false, estimator=DCStats)
```

The galley scheduler uses the sparsity patterns of the inputs to optimize the computation. The first set of inputs given to galley is used to optimize, and the `estimator` is used to estimate the sparsity of intermediate computations during optimization.
