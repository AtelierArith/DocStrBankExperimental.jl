```
zscore(X, [μ, σ])
```

Compute the z-scores of `X`, optionally specifying a precomputed mean `μ` and standard deviation `σ`. z-scores are the signed number of standard deviations above the mean that an observation lies, i.e. $(x - μ) / σ$.

`μ` and `σ` should be both scalars or both arrays. The computation is broadcasting. In particular, when `μ` and `σ` are arrays, they should have the same size, and `size(μ, i) == 1  || size(μ, i) == size(X, i)` for each dimension.
