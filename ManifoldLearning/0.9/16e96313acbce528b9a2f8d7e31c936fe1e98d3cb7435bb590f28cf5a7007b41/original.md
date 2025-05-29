```
fit(Isomap, data; k=12, maxoutdim=2, nntype=BruteForce)
```

Fit an isometric mapping model to `data`.

# Arguments

  * `data`: a matrix of observations. Each column of `data` is an observation.

# Keyword arguments

  * `k`: a number of nearest neighbors for construction of local subspace representation
  * `maxoutdim`: a dimension of the reduced space.
  * `nntype`: a nearest neighbor construction class (derived from `AbstractNearestNeighbors`)

# Examples

```julia
M = fit(Isomap, rand(3,100)) # construct Isomap model
R = predict(M)               # perform dimensionality reduction
```
