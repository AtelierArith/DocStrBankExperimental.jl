```julia
struct ℓDensityResult{T, S} <: BaytesDiff.ℓObjectiveResult
```

Stores result for log density and parameter for 'ℓobjective' evaluation at 'parameter'.

# Fields

  * `θᵤ::Any`: Parameter in unconstrained space.
  * `ℓθᵤ::Any`: Log density at θᵤ.
