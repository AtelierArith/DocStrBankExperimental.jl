```
SharedStatsStep{Alias, F<:Function, ById}
```

A [`StatsStep`](@ref) that is possibly shared by multiple instances of procedures that are subtypes of [`AbstractStatsProcedure`](@ref). See also [`PooledStatsProcedure`](@ref) and [`pool`](@ref).

# Fields

  * `step::StatsStep{Alias, F, ById}`: the `step` that may be shared.
  * `ids::Vector{Int}`: indices of procedures that share `step`.
