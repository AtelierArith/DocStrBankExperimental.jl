```julia
struct OptimTune{T<:ModelWrappers.Tagged, K, B<:BaytesCore.UpdateBool} <: BaytesCore.AbstractTune
```

Stores information used throughout optimization algorithms.

# Fields

  * `tagged::ModelWrappers.Tagged`: Tagged Parameter for Optimization routine
  * `kernel::Any`: Tuning arguments for individual Optimizer
  * `generated::BaytesCore.UpdateBool`: Boolean if generated quantities should be generated while sampling
  * `iter::BaytesCore.Iterator`: Current iteration number
