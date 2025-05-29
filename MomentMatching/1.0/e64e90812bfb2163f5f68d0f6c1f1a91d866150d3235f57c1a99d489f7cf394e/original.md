```julia
struct EstimationResult{S<:AbstractFloat, T<:Integer, U<:MomentMatching.AuxiliaryParameters, V<:MomentMatching.PredrawnShocks}
```

# Description

Structure to store output of matching moments estimation procedure.

# Fields

  * `npmm`: Numerical parameters
  * `aux`: Auxiliary inputs
  * `presh`: Predrawn shocks
  * `xlocstart`: Starting parameters - relevant when only local stage is performed
  * `pmm`: Moment estimation inputs
  * `fglo`: Objective function value in global stage, sorted in increasing order
  * `xglo`: Parameter combinations checked in global stage, sorted according to objective function value
  * `momglo`: Moments from model, global stage
  * `floc`: Objective function value in local stage, sorted in increasing order
  * `xloc`: Parameter combinations checked in local stage, sorted according to objective function value
  * `momloc`: Moments from model, local stage
  * `conv`: Logical, if true convergence criterion at minimum is satisfied in the local stage
