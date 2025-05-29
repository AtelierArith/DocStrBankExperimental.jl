```
seqd = DiscreteSequence(Gx, Gy, Gz, B1, Δf, ADC, t, Δt)
```

A sampled version of a Sequence struct, containing vectors for event amplitudes at specified times. DiscreteSequence is the struct used for simulation.

# Arguments

  * `Gx`: (`::AbstractVector{T<:Real}`, `[T/m]`) x-gradient vector
  * `Gy`: (`::AbstractVector{T<:Real}`, `[T/m]`) y-gradient vector
  * `Gz`: (`::AbstractVector{T<:Real}`, `[T/m]`) z-gradient vector
  * `B1`: (`::AbstractVector{Complex{T<:Real}}`, `[T]`) RF amplitude vector
  * `Δf`: (`::AbstractVector{T<:Real}`, `[Hz]`) RF carrier frequency displacement vector
  * `ADC`: (`::AbstractVector{Bool}`) ADC sample vector
  * `t`: (`::AbstractVector{T<:Real}`, `[s]`) time vector
  * `Δt`: (`::AbstractVector{T<:Real}`, `[s]`) delta time vector

# Returns

  * `seqd`: (`::DiscreteSequence`) DiscreteSequence struct
