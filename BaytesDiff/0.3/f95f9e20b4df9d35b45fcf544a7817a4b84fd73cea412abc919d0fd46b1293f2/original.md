```julia
struct ℓGradientResult{T<:(AbstractVector), S<:Real, G<:(AbstractVector)} <: BaytesDiff.ℓObjectiveResult
```

Stores result for log density, gradient, and parameter for 'ℓobjective' evaluation at 'parameter'.

# Fields

  * `θᵤ::AbstractVector`: Parameter in unconstrained space.
  * `ℓθᵤ::Real`: Log density at θᵤ.
  * `∇ℓθᵤ::AbstractVector`: Gradient of log density at θᵤ.
