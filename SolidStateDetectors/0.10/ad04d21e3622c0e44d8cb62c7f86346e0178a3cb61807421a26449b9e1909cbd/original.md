```
struct IsotropicChargeDriftModel{T <: SSDFloat} <: AbstractChargeDriftModel{T}
```

Charge drift model in which the electrons and holes drift along the electric field with a constant mobility in m²/Vs

## Fields

  * `μ_e::Union{RealQuantity, AbstractString}`: Mobility of the electrons in m²/Vs.
  * `μ_h::Union{RealQuantity, AbstractString}`: Mobility of the holes in m²/Vs.
