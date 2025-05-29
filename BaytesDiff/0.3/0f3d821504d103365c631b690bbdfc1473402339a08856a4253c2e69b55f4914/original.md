```julia
struct ObjectiveError <: Exception
```

Stores parameter in constrained space at which logdensity could not be evaluated.

# Fields

  * `msg::String`
  * `ℓθᵤ::Real`
  * `θ::NamedTuple`
  * `θᵤ::AbstractVector`
