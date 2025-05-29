```
piecewise_uniform(bounds, probs)
```

Samples a `Float64` value from a piecewise uniform continuous distribution.

There are `n` bins where `n = length(probs)` and `n + 1 = length(bounds)`. Bounds must satisfy `bounds[i] < bounds[i+1]` for all `i`. The probability density at `x` is zero if `x <= bounds[1]` or `x >= bounds[end]` and is otherwise `probs[bin] / (bounds[bin] - bounds[bin+1])` where `bounds[bin] < x <= bounds[bin+1]`.
