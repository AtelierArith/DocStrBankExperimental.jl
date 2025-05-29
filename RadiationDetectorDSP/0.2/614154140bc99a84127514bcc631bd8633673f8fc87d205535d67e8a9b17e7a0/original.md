```
struct SecondOrderCRFilter <: AbstractRadIIRFilter
```

A scond order CR highpass filter. The filter has an inverse [`InvSecondOrderCRFilter`](@ref).

Constructors:

  * `SecondOrderCRFilter(fields...)`

Fields:

  * `cr::Union{Real, Unitful.AbstractQuantity{<:Real}}`: time constant of the first exponential to be deconvolved
  * `cr2::Union{Real, Unitful.AbstractQuantity{<:Real}}`: time constant of the second exponential to be deconvolved
  * `f::Real`: the fraction faktor which the second exponential contributes
