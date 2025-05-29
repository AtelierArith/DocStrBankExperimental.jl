```julia
struct GeneralizedTurnStatistic{T}
```

Statistics for the identification of turning points. See Betancourt (2017, appendix), and subsequent discussion of improvements at [https://discourse.mc-stan.org/t/nuts-misses-u-turns-runs-in-circles-until-max-treedepth/9727/](https://discourse.mc-stan.org/t/nuts-misses-u-turns-runs-in-circles-until-max-treedepth/9727/). Momenta `p₋` and `p₊` are kept so that they can be added to `ρ` when combining turn statistics. Turn detection is always done by [`combine_turn_statistics`](@ref), which returns `nothing` in case of turning. A `GeneralizedTurnStatistic` should always correspond to a trajectory that is *not* turning (or a leaf node, where the concept does not apply).

# Fields

  * `ρ₋::Any`: momentum at the left edge of the trajectory
  * `ρ♯₋::Any`: p♯ at the left edge of the trajectory
  * `ρ₊::Any`: momentum at the right edge of the trajectory
  * `ρ♯₊::Any`: p♯ at the right edge of the trajectory
  * `ρₛ::Any`: sum of momenta along trajectory
