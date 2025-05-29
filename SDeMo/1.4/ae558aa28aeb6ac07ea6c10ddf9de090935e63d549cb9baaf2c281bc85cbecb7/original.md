```
noselection!(model; verbose::Bool = false, kwargs...)
```

Returns the model to the state where all variables are used.

All keyword arguments are passed to `train!`. For convenience, this version does not require a `folds` argument, as it would be unused anyway.
