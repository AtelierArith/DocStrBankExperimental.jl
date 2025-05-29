```
fit(LLE, data; k=12, maxoutdim=2, nntype=BruteForce, tol=1e-5)
```

Fit a locally linear embedding model to `data`.

# Arguments

  * `data`: a matrix of observations. Each column of `data` is an observation.

# Keyword arguments

  * `k`: a number of nearest neighbors for construction of local subspace representation
  * `maxoutdim`: a dimension of the reduced space.
  * `nntype`: a nearest neighbor construction class (derived from `AbstractNearestNeighbors`)
  * `tol`: an algorithm regularization tolerance

# Examples

```julia
M = fit(LLE, rand(3,100)) # construct LLE model
R = transform(M)          # perform dimensionality reduction
```
