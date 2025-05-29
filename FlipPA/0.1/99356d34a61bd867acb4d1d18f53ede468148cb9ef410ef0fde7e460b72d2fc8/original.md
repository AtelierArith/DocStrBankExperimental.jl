```
flippa(X; quantile=1.0, trials=100, threshold=0.0, comparison=FlipPA.UpperEdge(), rng=default_rng())
```

Estimate the signal rank of the data `X` using random signflips.

# Optional keyword arguments

  * `quantile` : quantile for the comparison, `default = 1.0`
  * `trials` : number of signflip trials to run, `default = 100`
  * `threshold` : threshold for the comparison, `default = 0.0`
  * `comparison` : comparison method to use, `default = FlipPA.UpperEdge()`
  * `rng` : random number generator, `default = default_rng()`
