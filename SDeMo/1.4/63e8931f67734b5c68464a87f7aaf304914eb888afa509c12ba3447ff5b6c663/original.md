```
backwardselection!(model, folds, pool; verbose::Bool = false, optimality=mcc, kwargs...)
```

Removes variables one at a time until the `optimality` measure stops increasing. Variables included in `pool` are not removed.

All keyword arguments are passed to `crossvalidate` and `train!`.
