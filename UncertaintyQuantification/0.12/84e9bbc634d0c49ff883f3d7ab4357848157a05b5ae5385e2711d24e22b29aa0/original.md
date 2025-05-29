```
CloughPenzien(ω::AbstractVector{<:Real}, S_0::Real, ω_f::Real, ζ_f::Real, ω_g::Real, ζ_g::Real)
```

Constructs a `CloughPenzien` instance representing a power spectral density function with the given parameters.

# Arguments / Parameters

  * `ω::AbstractVector{<:Real}`: A vector of angular frequencies.
  * `S_0::Real`: A scaling factor.
  * `ω_f::Real`: Frequency parameter for the first oscillator.
  * `ζ_f::Real`: Damping ratio for the first oscillator.
  * `ω_g::Real`: Frequency parameter for the second oscillator.
  * `ζ_g::Real`: Damping ratio for the second oscillator.

# Returns

A discretized `CloughPenzien` power spectral density function specified by given arguments (parameters).

# Example

```julia
w = 0:0.1:10
S_0 = 1.0
ω_f = 2.0
ζ_f = 0.05
ω_g = 3.0
ζ_g = 0.1
cp_psd = CloughPenzien(w, S_0, ω_f, ζ_f, ω_g, ζ_g)
```
