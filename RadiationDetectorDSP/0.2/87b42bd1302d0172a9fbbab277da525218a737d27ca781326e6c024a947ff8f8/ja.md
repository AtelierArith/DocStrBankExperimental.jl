```
struct SignalEstimator <: Function
```

指定された位置 `x` で信号を推定します。

使用法:

```julia
(f::SamplesOrWaveform)(input::RDWaveform, x::RealQuantity)
```

コンストラクタ:

  * `SignalEstimator(; fields...)`

フィールド:

  * `dni::RadiationDetectorDSP.DNIMethod`: デノイジングおよび補間方法
