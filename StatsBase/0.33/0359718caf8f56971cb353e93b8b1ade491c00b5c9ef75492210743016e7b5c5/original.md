```
proportions(x, k::Integer, [wv::AbstractWeights])
```

Return the proportion of integers in 1 to `k` that occur in `x`.

If a vector of weights `wv` is provided, the proportion of weights is computed rather than the proportion of raw counts.
