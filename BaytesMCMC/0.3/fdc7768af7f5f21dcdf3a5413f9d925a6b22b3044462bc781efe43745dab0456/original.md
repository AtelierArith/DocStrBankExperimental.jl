```julia
struct DualAverage{T<:AbstractFloat}
```

Contains DualAverage tuning information and runtime parameter.

# Fields

  * `adaption::BaytesMCMC.DualAverageParameter`
  * `μ::AbstractFloat`: Upwards bias for target acceptance rate - proposals are biased upwards to stay away from 0.
  * `t::Int64`: Time update, starts with 0
  * `H̄::AbstractFloat`: Average part of first equation in Hoffman(2014), p 1607, (6)
  * `logϵ::AbstractFloat`: Log step
  * `logϵ̄::AbstractFloat`: AVERAGED log step
