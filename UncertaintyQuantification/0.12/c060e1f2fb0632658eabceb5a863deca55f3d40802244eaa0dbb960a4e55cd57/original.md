```
KanaiTajimi(ω::AbstractVector{<:Real}, S_0::Real, ω_0::Real, ζ::Real) -> KanaiTajimi
```

Constructs a `KanaiTajimi` instance representing a power spectral density function with the given parameters.

# Arguments

  * `ω::AbstractVector{<:Real}`: A vector of angular frequencies.
  * `S_0::Real`: A scaling factor.
  * `ω_0::Real`: Natural frequency of the oscillator.
  * `ζ::Real`: Damping ratio of the oscillator.

# Returns

A discretized `KanaiTajimi` power spectral density function specified by given arguments (parameters).

# Example

```julia
w = 0:0.1:10
S_0 = 1.0
ω_0 = 2.0
ζ = 0.05
kt = KanaiTajimi(w, S_0, ω_0, ζ)
```
