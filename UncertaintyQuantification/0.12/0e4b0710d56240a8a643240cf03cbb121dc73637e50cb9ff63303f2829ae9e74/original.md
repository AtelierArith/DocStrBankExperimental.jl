```
SpectralRepresentation(psd::AbstractPowerSpectralDensity, time::AbstractVector{<:Real}, name::Symbol) -> SpectralRepresentation
```

Constructs a `SpectralRepresentation` instance representing a stochastic process generated using the spectral representation method.

# Arguments

  * `psd::AbstractPowerSpectralDensity`: An instance of a power spectral density model.
  * `time::AbstractVector{<:Real}`: A vector of time points.
  * `name::Symbol`: A symbol representing the name of the process.

# Returns

A `SpectralRepresentation` instance with the given arguments (parameters).

# Example

```julia
w = 0:0.1:10
S_0 = 1.0
ω_f = 2.0
ζ_f = 0.05
ω_g = 3.0
ζ_g = 0.1
psd = CloughPenzien(w, S_0, ω_f, ζ_f, ω_g, ζ_g)
t = 0:0.1:10
name = :process1
sr = SpectralRepresentation(psd, t, name)
```
