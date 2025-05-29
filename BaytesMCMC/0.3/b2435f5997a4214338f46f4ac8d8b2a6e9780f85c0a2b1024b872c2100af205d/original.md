```julia
struct ConfigStepsize{A<:BaytesCore.UpdateBool, B<:BaytesCore.UpdateBool}
```

Default configuration for stepsize adaption.

# Fields

  * `ϵ::Float64`: Initial Discretization size
  * `stepsizeadaption::BaytesCore.UpdateBool`: Step size adaption
  * `initialstepsize::BaytesCore.UpdateBool`: Boolean if initial stepsize should be estimated
