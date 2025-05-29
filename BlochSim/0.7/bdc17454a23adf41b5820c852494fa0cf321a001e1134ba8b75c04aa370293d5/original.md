```
RF(waveform, Δt, [Δθ], [grad]) <: AbstractRF
```

Represents an RF pulse with the given (possibly complex-valued) waveform (G) and time step `Δt` (ms). `Δθ` is additional phase added to the waveform (defaults to `0`), and `grad` is the B0 gradient that is turned on during the RF pulse (defaults to `Gradient(0, 0, 0)`, i.e., turned off).

# Properties

  * `α::Vector{<:Real}`: Instantaneous flip angles (rad) at each time point; computed from the magnitude of `waveform`
  * `θ::Vector{<:Real}`: Instantaneous phase (rad) at each time point; computed from the phase of `waveform`
  * `Δt::Real`: Time step (ms)
  * `Δθ_initial::Real`: Phase added to `θ` before any phase-cycling increment has been applied
  * `Δθ::Ref{<:Real}`: Phase to be added to `θ`; can be updated to simulate phase-cycling/RF spoiling
  * `grad`: Gradient applied during the RF pulse

      * `::Gradient`: Constant gradient
      * `::Vector{<:Gradient}`: Time-varying gradient
