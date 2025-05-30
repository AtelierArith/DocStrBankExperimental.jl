```
fit_mnf(raster::Union{<:AbstractRasterStack, <:AbstractRaster}, noise_covariance::Matrix; stats_fraction=1.0)
fit_mnf(signatures::Matrix, noise_covariance::Matrix; stats_fraction=1.0)
```

Fit a Minimum Noise Fraction (MNF) transformation to the given `AbstractRasterStack` or `AbstractRaster`.

# Parameters

  * `raster`: The `AbstractRaster` or `AbstractRasterStack` on which to fit the MNF transformation.
  * `signatures`: An n x b matrix of spectral signatures where n is the number of signatures and b is the number of bands.
  * `noise_sample`: A homogenous (spectrally uniform) region extracted from `raster` for calculating the noise covariance matrix.
  * `smooth`: The MNF transform cannot be computed if any band in `noise_sample` has zero variance. To correct this, you may wish to introduce a small smoothing term (true by default).
