```
struct FirstOrderIIR{T<:RealQuantity} <: AbstractRadIIRFilter
```

A [biquad filter](https://en.wikipedia.org/wiki/Digital_biquad_filter).

Constructors:

  * `FirstOrderIIR(fields...)`

Fields:

  * `b_01::Tuple{T, T} where T<:Union{Real, Unitful.AbstractQuantity{<:Real}}`: Coefficients b*0 to b*1
  * `a_1::Tuple{T} where T<:Union{Real, Unitful.AbstractQuantity{<:Real}}`: Coefficient a*1, a*0 equals one implicitly
