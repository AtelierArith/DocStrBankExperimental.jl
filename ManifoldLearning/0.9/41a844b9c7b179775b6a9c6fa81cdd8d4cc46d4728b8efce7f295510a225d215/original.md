```
fit(LEM, data; k=12, maxoutdim=2, ɛ=1.0, nntype=BruteForce)
```

Fit a Laplacian eigenmaps model to `data`.

# Arguments

  * `data`: a matrix of observations. Each column of `data` is an observation.

# Keyword arguments

  * `k`: a number of nearest neighbors for construction of local subspace representation
  * `maxoutdim`: a dimension of the reduced space.
  * `nntype`: a nearest neighbor construction class (derived from `AbstractNearestNeighbors`)
  * `ɛ`: a Gaussian kernel variance (the scale parameter)
  * `laplacian`: a form of the Laplacian matrix used for spectral decomposition

      * `:unnorm`: an unnormalized Laplacian
      * `:sym`: a symmetrically normalized Laplacian
      * `:rw`: a random walk normalized Laplacian

# Examples

```julia
M = fit(LEM, rand(3,100)) # construct Laplacian eigenmaps model
R = predict(M)          # perform dimensionality reduction
```
