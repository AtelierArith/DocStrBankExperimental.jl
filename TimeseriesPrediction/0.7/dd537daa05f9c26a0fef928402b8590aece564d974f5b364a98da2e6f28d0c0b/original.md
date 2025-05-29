```
PCAEmbedding(s, em::AbstractSpatialEmbedding; kwargs...) → embedding
```

A spatio temporal delay coordinates structure with Principal Component Analysis as a means of dimension reduction, `embedding` can be used as a functor:

```julia
embedding(rvec, s, t, α)
```

which operates inplace on `rvec` and reconstructs vector from spatial time series `s` at timestep `t` and cartesian index `α`.

To instantiate this `embedding`, give the data to be reconstructed `s` as well as an instance of [`SpatioTemporalEmbedding`](@ref) to `PCAEmbedding`.

## Keyword Arguments

  * `pratio = 0.99` : Ratio of variances that needs to be preserved in low-dimensional PCA-reconstruction.
  * `maxoutdim = 25`: Upper limit for output dimension. May break `pratio` criterion.
  * `every_t = 1` : Speed up computation by only using every n-th point in time.
  * `every_α = 1` : Speed up computation further by only using every n-th point in space (linear indexing).

To set the output dimension to a certain value `X`, pass `pratio=1, maxoutdim=X`.
