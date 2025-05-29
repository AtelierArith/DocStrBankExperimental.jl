```julia
struct ConfigStepnumber{A<:BaytesCore.UpdateBool}
```

Default configuration for stepsize adaption.

# Fields

  * `stepnumberadaption::BaytesCore.UpdateBool`: Step Number adaption
  * `steps::Int64`: Initial number of Steps
  * `maxsteps::Int64`: Maximal number of steps
  * `∫dt::Float64`: Desired Integration time
