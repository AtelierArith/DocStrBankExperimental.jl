```
zscore!([Z], X, μ, σ)
```

Compute the z-scores of an array `X` with mean `μ` and standard deviation `σ`. z-scores are the signed number of standard deviations above the mean that an observation lies, i.e. $(x - μ) / σ$.

If a destination array `Z` is provided, the scores are stored in `Z` and it must have the same shape as `X`. Otherwise `X` is overwritten.
