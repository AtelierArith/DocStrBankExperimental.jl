```
nquantile(x, n::Integer)
```

Return the n-quantiles of collection `x`, i.e. the values which partition `v` into `n` subsets of nearly equal size.

Equivalent to `quantile(x, [0:n]/n)`. For example, `nquantiles(x, 5)` returns a vector of quantiles, respectively at `[0.0, 0.2, 0.4, 0.6, 0.8, 1.0]`.
