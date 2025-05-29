```
abstract type AbstractRadSigFilterInstance{FT<:FilteringType}
```

信号フィルターインスタンスのための抽象型。フィルターインスタンスは、特定の長さと数値型の入力および出力に特化しています。

フィルターインスタンスは `(fi::SomeFilterInstance)(input)` のように呼び出すことができ、特化したブロードキャスティングが付属しています。

`AbstractRadSigFilterInstance` のサブタイプは以下を実装しなければなりません。

  * `RadiationDetectorDSP.rdfilt!(output, fi::SomeFilterInstance, input)`
  * `RadiationDetectorDSP.flt_output_smpltype(fi::SomeFilterInstance)`
  * `RadiationDetectorDSP.flt_input_smpltype(fi::SomeFilterInstance)`
  * `RadiationDetectorDSP.flt_output_length(fi::SomeFilterInstance)`
  * `RadiationDetectorDSP.flt_input_length(fi::SomeFilterInstance)`
  * `RadiationDetectorDSP.flt_output_time_axis(fi::SomeFilterInstance, time::AbstractVector{<:RealQuantity})`

可逆フィルターインスタンスは以下を実装する必要があります。

  * `InverseFunctions.inverse(fi::SomeFilterInstance)`

デフォルトメソッドは以下に対して実装されています。

  * `RadiationDetectorDSP.rdfilt(fi::AbstractRadSigFilterInstance, x::AbstractSamples)`
  * `RadiationDetectorDSP.rdfilt(fi::AbstractRadSigFilterInstance, wf::RDWaveform)`
  * `RadiationDetectorDSP.bc_rdfilt(fi::AbstractRadSigFilterInstance, inputs)`

`RadiationDetectorSignals.RDWaveform` に対して動作するデフォルトメソッドは [`RadiationDetectorDSP.flt_output_time_axis`](@ref) を必要とします。
