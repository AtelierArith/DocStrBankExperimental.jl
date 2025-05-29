```
abstract type AbstractRadSigFilterInstance{FT<:FilteringType}
```

Abstract type for signal filter instances. Filter instances are specilized to a specific length and numerical type of input and output.

Filter instances are callable as `(fi::SomeFilterInstance)(input)` and come with specialized broadcasting.

Subtypes of `AbstractRadSigFilterInstance` must implement

  * `RadiationDetectorDSP.rdfilt!(output, fi::SomeFilterInstance, input)`
  * `RadiationDetectorDSP.flt_output_smpltype(fi::SomeFilterInstance)`
  * `RadiationDetectorDSP.flt_input_smpltype(fi::SomeFilterInstance)`
  * `RadiationDetectorDSP.flt_output_length(fi::SomeFilterInstance)`
  * `RadiationDetectorDSP.flt_input_length(fi::SomeFilterInstance)`
  * `RadiationDetectorDSP.flt_output_time_axis(fi::SomeFilterInstance, time::AbstractVector{<:RealQuantity})`

Invertible filter instances should implement

  * `InverseFunctions.inverse(fi::SomeFilterInstance)`

Default methods are implemented for

  * `RadiationDetectorDSP.rdfilt(fi::AbstractRadSigFilterInstance, x::AbstractSamples)`
  * `RadiationDetectorDSP.rdfilt(fi::AbstractRadSigFilterInstance, wf::RDWaveform)`
  * `RadiationDetectorDSP.bc_rdfilt(fi::AbstractRadSigFilterInstance, inputs)`

The default methods that operate on `RadiationDetectorSignals.RDWaveform`s require [`RadiationDetectorDSP.flt_output_time_axis`](@ref).
