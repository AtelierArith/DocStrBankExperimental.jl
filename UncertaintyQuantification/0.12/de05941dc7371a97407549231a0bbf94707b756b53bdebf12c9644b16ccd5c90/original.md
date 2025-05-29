```
ShinozukaDeodatis(ω::AbstractVector{<:Real}, σ::Real, b::Real)
```

Constructs a `ShinozukaDeodatis` instance representing a power spectral density function with the given parameters.

# Arguments

  * `ω::AbstractVector{<:Real}`: A vector of angular frequencies.
  * `σ::Real`: A hyperparamter related to the variance of the stochastic process.
  * `b::Real`: A parameter related to the correlation length of the stochastic process.

# Returns

A discretized `ShinozukaDeodatis` instance with the power spectral density function specified by given arguments (parameters).

# Example

```julia
w = 0:0.1:10
σ = 1.0
b = 0.5
sd = ShinozukaDeodatis(w, σ, b)
```
