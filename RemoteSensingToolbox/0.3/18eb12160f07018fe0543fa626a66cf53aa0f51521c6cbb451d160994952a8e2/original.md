```
fit_pca(raster::Union{<:AbstractRasterStack, <:AbstractRaster}; method=:cov, stats_fraction=1.0)
fit_pca(signatures::Matrix; method=:cov, stats_fraction=1.0)
```

Fit a Principal Component Analysis (PCA) transformation to the given raster or spectral signatures.

# Parameters

  * `raster`: The `AbstractRaster` or `AbstractRasterStack` on which to fit the PCA transformation.
  * `signatures`: An nxb matrix of spectral signatures where n is the number of signatures and b is the number of bands.

# Keywords

  * `method`: Either `:cov` or `:cor`, depending on whether we want to use the covariance or correlation matrix for computing the PCA rotation.
  * `stats_fraction`: The fraction of pixels to use when computing the covariance (or correlation) matrix. Values less than 1.0 will speed up computation at the cost of precision.
