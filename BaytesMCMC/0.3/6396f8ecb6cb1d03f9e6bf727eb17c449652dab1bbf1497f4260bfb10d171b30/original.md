```julia
struct ConfigProposal{A<:BaytesCore.UpdateBool, M<:BaytesMCMC.MatrixMetric, F}
```

Default configuration for posterior Covariance Matrix adaption.

# Fields

  * `proposaladaption::BaytesCore.UpdateBool`: Boolean if Posterior covariance for proposal steps is adapted.
  * `metric::BaytesMCMC.MatrixMetric`: Covariance estimate metric: MDense(), MDiagonal(), MUnit()
  * `shrinkage::Float64`: Shrinkage parameter towards Diagonal Matrix with equal variance
  * `covariance::Any`: Initial covariance matrix for proposal distribution. Kept throughout sampling if 'proposaladaption' is set to UpdateFalse. By default not initiated.
