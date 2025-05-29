```
struct FirstOrderIIR{T<:RealQuantity} <: AbstractRadIIRFilter
```

[バイコアフィルタ](https://en.wikipedia.org/wiki/Digital_biquad_filter)。

コンストラクタ:

  * `FirstOrderIIR(fields...)`

フィールド:

  * `b_01::Tuple{T, T} where T<:Union{Real, Unitful.AbstractQuantity{<:Real}}`: コエフィシエント b*0 から b*1
  * `a_1::Tuple{T} where T<:Union{Real, Unitful.AbstractQuantity{<:Real}}`: コエフィシエント a*1、a*0 は暗黙的に1に等しい
