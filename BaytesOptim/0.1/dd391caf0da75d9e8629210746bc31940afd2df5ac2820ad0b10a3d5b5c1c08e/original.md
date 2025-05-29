```julia
struct CustomAlgorithmTune{T<:ModelWrappers.Tagged, B<:BaytesCore.UpdateBool} <: BaytesCore.AbstractTune
```

Stores information used throughout custom algorithm.

# Fields

  * `tagged::ModelWrappers.Tagged`: Tagged Parameter for Algorithm routine
  * `generated::BaytesCore.UpdateBool`: Boolean if generated quantities should be generated while sampling
  * `iter::BaytesCore.Iterator`: Current iteration number
