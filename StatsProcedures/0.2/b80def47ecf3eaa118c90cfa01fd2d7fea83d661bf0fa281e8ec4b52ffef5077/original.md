```
PooledStatsProcedure
```

A collection of procedures and shared steps.

An instance of `PooledStatsProcedure` is indexed and iterable among the shared steps in a way that helps avoid repeating identical steps. See also [`pool`](@ref).

# Fields

  * `procs::Vector{AbstractStatsProcedure}`: a collection of [`AbstractStatsProcedure`](@ref)s.
  * `steps::Vector{SharedStatsStep}`: sorted [`SharedStatsStep`](@ref)s.
