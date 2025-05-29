```julia
struct ℓHessianResult{T<:(AbstractVector), S<:Real, G<:(AbstractVector), H<:(AbstractMatrix)} <: BaytesDiff.ℓObjectiveResult
```

Stores result for log density, gradient, hessian and parameter for 'ℓobjective' evaluation at 'parameter'.

# Fields

  * `θᵤ::AbstractVector`: Parameter in unconstrained space.
  * `ℓθᵤ::Real`: Log density at θᵤ.
  * `∇ℓθᵤ::AbstractVector`: Gradient of log density at θᵤ.
  * `Δℓθᵤ::AbstractMatrix`: Hessian of log density at θᵤ.
