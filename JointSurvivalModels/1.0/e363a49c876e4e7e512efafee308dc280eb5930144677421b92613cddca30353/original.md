```
HazardBasedDistribution <: ContinuousUnivariateDistribution
```

`HazardBasedDistribution` is a type that builds a distribution based  on a hazard function.

To use this type to formulate a distribution yourself: implement a struct and the hazard function.

```julia
struct LogLogistic <: HazardBasedDistribution
    α::Real
    β::Real
end

function JointSurvivalModels.hazard(dist::LogLogistic, t::Real)
    α, β  = dist.α, dist.β
    return ((β / α) * (t / α) ^ (β - 1)) / (1 + (t / α) ^ β)
end
```

`HazardBasedDistribution` implements numeric integration to calculate the  cumulative hazard and builds a distribution based it. To generate samples it solves an ODE and applies inverse transform sampling.
