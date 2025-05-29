```
forwardselection!(model, folds; verbose::Bool = false, optimality=mcc, kwargs...)
```

Adds variables one at a time until the `optimality` measure stops increasing.

All keyword arguments are passed to `crossvalidate` and `train!`.
