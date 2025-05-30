```
estimate_noise(raster::Union{<:AbstractRaster, <:AbstractRasterStack}; smooth=false)
```

Estimate the noise covariance matrix for the given raster.

Uses the Minimum/Maximum Autocorrelation Factor proposed by [Switzer and Green](https://www.researchgate.net/publication/239665649_MinMax_Autocorrelation_factors_for_multivariate_spatial_imagery_Technical_Report_6).

For best results, the provided raster should be spectrally homoegenous (e.g., an open field or body of water).

# Parameters

  * `raster`: An `AbstractRaster` or `AbstractRasterStack`.
  * `smooth`: Numerical stability requires that no bands have a variance of zero. A smoothing term can be applied to ensure that this is the case.

# Example

```julia
using RemoteSensingToolbox, Rasters

# Load Data
src = DESIS("DESIS-HSI-L2A-DT0485529167_001-20220712T223540-V0220")
desis = decode(DESIS, Raster(src, :Bands))

# Extract Homogenous Region of Interest
roi = desis[X(1019:1040), Y(550:590)]

# Estimate Noise
ncm = estimate_noise(roi, smooth=true)
```
