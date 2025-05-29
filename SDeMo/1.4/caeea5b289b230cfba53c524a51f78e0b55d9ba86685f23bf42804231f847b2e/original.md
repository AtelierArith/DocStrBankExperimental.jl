```
montecarlo(y, X; n = 100, kwargs...)
```

Returns `n` (def. `100`) samples of `holdout`. Other keyword arguments are passed to `holdout`.

This method returns a vector of tuples, with each entry have the training data first, and the validation data second.
