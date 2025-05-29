```julia
struct MatrixTune{A<:BaytesMCMC.MatrixMetric}
```

Mass and Covariance Matrix specification for MCMC sampler, relevant for Euclidean Metric.

# Fields

  * `metric::BaytesMCMC.MatrixMetric`: Dense, Diagonal or Unit Mass Matrix.
  * `shrinkage::Float64`: Shrinkage parameter for Covariance estimation.
