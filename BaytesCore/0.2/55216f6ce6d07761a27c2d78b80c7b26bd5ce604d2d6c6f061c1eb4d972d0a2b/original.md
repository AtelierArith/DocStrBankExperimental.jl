```julia
struct JitterTune{B<:BaytesCore.UpdateBool}
```

Container that determines if jittering has to be applied

# Fields

  * `adaption::BaytesCore.UpdateBool`: Bolean if adaptive jittering is applied. If false, always max steps are jittered.
  * `Nsteps::BaytesCore.Iterator`: Number of jitttering steps performed while jittering
  * `threshold::Float64`: Jittering threshold for correlation of parameter.
  * `min::Int64`: Minimum amount of jittering steps.
  * `max::Int64`: Maximum amount of jittering steps.
