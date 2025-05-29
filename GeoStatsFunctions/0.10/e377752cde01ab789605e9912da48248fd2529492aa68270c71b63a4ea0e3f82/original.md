```
EmpiricalVariogram(data, var₁, var₂=var₁; [options])
```

Computes the empirical (a.k.a. experimental) omnidirectional (cross-)variogram for variables `var₁` and `var₂` stored in geospatial `data`.

## Options

  * nlags     - number of lags (default to `20`)
  * maxlag    - maximum lag in length units (default to 1/2 of minimum side of bounding box)
  * distance  - custom distance function (default to `Euclidean` distance)
  * estimator - variogram estimator (default to `:matheron` estimator)
  * algorithm - accumulation algorithm (default to `:ball`)

Available estimators:

  * `:matheron` - simple estimator based on squared differences
  * `:cressie`  - robust estimator based on 4th power of differences

Available algorithms:

  * `:full` - loop over all pairs of points in the data
  * `:ball` - loop over all points inside maximum lag ball

All implemented algorithms produce the exact same result. The `:ball` algorithm is considerably faster when the maximum lag is much smaller than the bounding box of the domain of the data.

See also: [`DirectionalVariogram`](@ref), [`PlanarVariogram`](@ref), [`EmpiricalVariogramSurface`](@ref).

## References

  * Chilès, JP and Delfiner, P. 2012. [Geostatistics: Modeling Spatial Uncertainty](https://onlinelibrary.wiley.com/doi/book/10.1002/9781118136188)
  * Webster, R and Oliver, MA. 2007. [Geostatistics for Environmental Scientists](https://onlinelibrary.wiley.com/doi/book/10.1002/9780470517277)
  * Hoffimann, J and Zadrozny, B. 2019. [Efficient variography with partition variograms](https://www.sciencedirect.com/science/article/pii/S0098300419302936)
