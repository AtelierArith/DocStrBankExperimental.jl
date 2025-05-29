```
fit(TSNE, data; p=30, maxoutdim=2, kwargs...)
```

Fit a t-SNE model to `data`.

# Arguments

  * `data`: a matrix of observations. Each column of `data` is an observation.

# Keyword arguments

  * `p`: a perplexity parameter (*defaut* `30`).
  * `maxoutdim`: a dimension of the reduced space (*defaut* `2`).
  * `maxiter`: a total number of iterations for the search algorithm (*defaut* `800`).
  * `exploreiter`: a number of iterations for the exploration stage of the search algorithm (*defaut* `200`).
  * `tol`: a tolerance threshold (*default* `1e-7`).
  * `exaggeration`: a tightness control parameter between the original and the reduced space (*defaut* `12`).
  * `initialize`: an initialization parameter for the embedding (*defaut* `:pca`).
  * `rng`: a random number generator object for initialization of the initial embedding.
  * `nntype`: a nearest neighbor construction class (derived from `AbstractNearestNeighbors`)

# Examples

```julia
M = fit(TSNE, rand(3,100)) # construct t-SNE model
R = predict(M)             # perform dimensionality reduction
```
