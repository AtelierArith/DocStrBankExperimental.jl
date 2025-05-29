```
LazyTensor(b1[, b2], indices, operators[, factor=1])
```

Lazy implementation of a tensor product of operators.

The suboperators are stored in the `operators` field. The `indices` field specifies in which subsystem the corresponding operator lives. Note that these must be sorted. Additionally, a factor is stored in the `factor` field which allows for fast multiplication with numbers.
