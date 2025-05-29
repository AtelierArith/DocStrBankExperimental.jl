```
smoothen(noisy::AbstractVector, b)
```

Smoothen the array `noisy` by averaging over a sliding window of length `b` and wrapping `noisy` periodically. The `mean(noisy)` is preserved.
