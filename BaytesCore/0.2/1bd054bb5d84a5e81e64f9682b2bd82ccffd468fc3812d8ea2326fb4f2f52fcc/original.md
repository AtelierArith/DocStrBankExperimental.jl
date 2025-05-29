```julia
struct IterationTempering{A<:BaytesCore.UpdateBool, T<:AbstractFloat} <: BaytesCore.TemperingMethod
```

Tuning container for iteration uptdates of temperature.

# Fields

  * `adaption::BaytesCore.UpdateBool`: Checks if temperature will be updated after new iterations
  * `initial::BaytesCore.ValueHolder{T} where T<:AbstractFloat`: Initial temperature for tempering.
  * `parameter::BaytesCore.TemperingParameter`: Tuning parameter for temperature adjustment.
