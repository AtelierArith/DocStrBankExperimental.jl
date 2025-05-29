```julia
struct EstimationSetup{U<:MomentMatching.EstimationMode}
```

# Description

Structure to store setup of matching moments estimation procedure.

# Fields

  * `mode`: Estimation mode.
  * `modelname`: Submethod for estimation. String encoding which parameters and how are estimated.
  * `typemom`: Submethod for estimation. String encoding which moments are targeted.
