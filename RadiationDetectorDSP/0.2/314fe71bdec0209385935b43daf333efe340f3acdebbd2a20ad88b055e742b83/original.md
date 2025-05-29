```
struct BiquadFilter{T<:RealQuantity} <: AbstractRadIIRFilter
```

A [biquad filter](https://en.wikipedia.org/wiki/Digital_biquad_filter).

Constructors:

  * `BiquadFilter(fields...)`

Fields:

  * `b_012::Tuple{T, T, T} where T<:Union{Real, Unitful.AbstractQuantity{<:Real}}`: Coefficients b*0 to b*2
  * `a_12::Tuple{T, T} where T<:Union{Real, Unitful.AbstractQuantity{<:Real}}`: Coefficients a*1 to a*2, a_0 equals one implicitly
