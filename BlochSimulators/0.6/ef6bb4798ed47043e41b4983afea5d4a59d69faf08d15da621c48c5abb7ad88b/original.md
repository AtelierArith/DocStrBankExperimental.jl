```
pSSFP3D{T<:AbstractFloat,N,U<:AbstractVector{Complex{T}},V<:Number} <: IsochromatSimulator{T}
```

This struct is used to simulate an inversion-recovery, gradient-balanced, transient-state sequence with varying flip angle scheme based on the isochromat model. The TR and TE are fixed throughout the sequence. The RF excitation waveform can be discretized in time but no slice profile mechanism is provided. The sequence also uses an 'α/2' prepulse after the inversion.

Within each TR, multiple time steps are used to simulate the RF excitation. Then, in one time step we go from the end of the RF excitation to the echo time (applying slice refocussing gradient, T₂ decay and B₀ rotation), and again in one time step from the echo time to the start of the next RF excitation.

# Fields

  * `RF_train::U` Vector with flip angle for each TR with abs.(RF*train) the RF flip angles in degrees and   angle.(RF*train) should be the RF phases in degrees.
  * `TR::T`: Repetition time in seconds, assumed constant during the sequence
  * `γΔtRF::SVector{N}{V}`: Time-discretized RF waveform, normalized to flip angle of 1 degree
  * `Δt::NamedTuple{(:ex, :inv, :pr),NTuple{3,T}}`: Time interval for each sample of excitation pulse (ex),   inversion delay (inv) and time between RF and TE (pr)
