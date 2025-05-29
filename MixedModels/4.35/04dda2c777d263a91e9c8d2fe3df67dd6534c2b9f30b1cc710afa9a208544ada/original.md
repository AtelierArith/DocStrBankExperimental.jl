```
GHnorm(k::Int)
```

Return the (unique) GaussHermiteNormalized{k} object.

The function values are stored (memoized) when first evaluated.  Subsequent evaluations for the same `k` have very low overhead.
