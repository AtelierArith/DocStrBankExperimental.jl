```
struct InvSecondOrderCRFilter <: AbstractRadIIRFilter
```

Inverse of [`SecondOrderCRFilter`](@ref). Apply a double pole-zero cancellation using the provided time constants to the waveform.

Constructors:

  * `InvSecondOrderCRFilter(fields...)`

Fields:

  * `cr::Union{Real, Unitful.AbstractQuantity{<:Real}}`: time constant of the first exponential to be deconvolved
  * `cr2::Union{Real, Unitful.AbstractQuantity{<:Real}}`: time constant of the second exponential to be deconvolved
  * `f::Real`: the fraction faktor which the second exponential contributes
