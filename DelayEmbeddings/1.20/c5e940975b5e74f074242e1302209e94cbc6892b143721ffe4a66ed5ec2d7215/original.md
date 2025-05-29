```
exponential_decay_fit(x, y, weight = :equal) -> τ
```

Perform a least square fit of the form `y = exp(-x/τ)` and return `τ`. Taken from:  http://mathworld.wolfram.com/LeastSquaresFittingExponential.html. Assumes equal lengths of `x, y` and that `y ≥ 0`.

To use the method that gives more weight to small values of `y`, use `weight = :small`.
