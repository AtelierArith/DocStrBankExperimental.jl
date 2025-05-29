```
struct ConvolutionFilter{T<:RealQuantity} <: AbstractRadFIRFilter
```

A [FIR filter](https://en.wikipedia.org/wiki/Finite_impulse_response) defined by it's filter taps, applied via convolution with the input signal.

Constructors:

  * `ConvolutionFilter(fields...)`

Fields:

  * `method::RadiationDetectorDSP.ConvolutionMethod`: Convolution method
  * `coeffs::AbstractVector{T} where T<:Union{Real, Unitful.AbstractQuantity{<:Real}}`: Filter taps
  * `offset::Int64`: Time axis offset
