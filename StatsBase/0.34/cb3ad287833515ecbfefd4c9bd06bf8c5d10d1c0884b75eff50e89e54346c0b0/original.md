```
proportions(x, levels=span(x), [wv::AbstractWeights])
```

Return the proportion of values in the range `levels` that occur in `x`. Equivalent to `counts(x, levels) / length(x)`.

If a vector of weights `wv` is provided, the proportion of weights is computed rather than the proportion of raw counts.
