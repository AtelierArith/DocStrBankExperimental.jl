```julia
struct ParMM{S<:AbstractFloat}
```

# Description

Structure to store matching moments estimation inputs.

# Fields

  * `lb_global`: Lower bound for parameters in global stage
  * `ub_global`: Upper bound for parameters in global stage
  * `lb_hard`: Hard lower bound for parameters - being outside brings penalty in local stage
  * `ub_hard`: Hard upper bound for parameters - being outside brings penalty in local stage
  * `labels`: Labels of estimated parameters
  * `momdat`: Moments from the data to match
  * `mmomdat`: Normalizing factor moments from the data to match
  * `W`: Weighting matrix
  * `mdifrec`: Predetermined quantity to re-center moment condition
