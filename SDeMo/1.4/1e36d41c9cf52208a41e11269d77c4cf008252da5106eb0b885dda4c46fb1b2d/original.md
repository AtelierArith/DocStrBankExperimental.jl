```
forwardselection!(model, folds, pool; verbose::Bool = false, optimality=mcc, kwargs...)
```

Adds variables one at a time until the `optimality` measure stops increasing. The variables in `pool` are added at the start.

All keyword arguments are passed to `crossvalidate` and `train!`.
