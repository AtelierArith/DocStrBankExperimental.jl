```
struct ConvolutionFilter{T<:RealQuantity} <: AbstractRadFIRFilter
```

入力信号との畳み込みを介して適用されるフィルタタップによって定義される[FIRフィルタ](https://en.wikipedia.org/wiki/Finite_impulse_response)。

コンストラクタ:

  * `ConvolutionFilter(fields...)`

フィールド:

  * `method::RadiationDetectorDSP.ConvolutionMethod`: 畳み込み方法
  * `coeffs::AbstractVector{T} where T<:Union{Real, Unitful.AbstractQuantity{<:Real}}`: フィルタタップ
  * `offset::Int64`: 時間軸オフセット
