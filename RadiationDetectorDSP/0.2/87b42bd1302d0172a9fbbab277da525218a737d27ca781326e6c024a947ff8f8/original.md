```
struct SignalEstimator <: Function
```

Estimates a signal at a given position `x`.

Usage:

```julia
(f::SamplesOrWaveform)(input::RDWaveform, x::RealQuantity)
```

Constructors:

  * `SignalEstimator(; fields...)`

Fields:

  * `dni::RadiationDetectorDSP.DNIMethod`: denoising and interpolation method
