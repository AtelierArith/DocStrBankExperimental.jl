```julia
struct PhasePoint{T<:BaytesDiff.ℓObjectiveResult, S<:Real}
```

A point in phase space, consists of a position BaytesDiff.ℓObjectiveResult and a momentum ρ.

# Fields

  * `result::BaytesDiff.ℓObjectiveResult`: BaytesDiff.ℓObjectiveResult container
  * `ρ::Vector{S} where S<:Real`: Momentum
