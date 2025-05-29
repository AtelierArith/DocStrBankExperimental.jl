```julia
struct JointTempering{A<:BaytesCore.UpdateBool, T<:AbstractFloat} <: BaytesCore.TemperingMethod
```

Tuning container for joint uptdates of temperature.

# Fields

  * `adaption::BaytesCore.UpdateBool`: Checks if temperature will be updated after new iterations
  * `val::BaytesCore.ValueHolder{T} where T<:AbstractFloat`: current temperature.
  * `ESSTarget::BaytesCore.ValueHolder{T} where T<:AbstractFloat`: Target Effective Sample Size.
  * `weights::Vector{T} where T<:AbstractFloat`: Buffer for weights used to adapt temperature
