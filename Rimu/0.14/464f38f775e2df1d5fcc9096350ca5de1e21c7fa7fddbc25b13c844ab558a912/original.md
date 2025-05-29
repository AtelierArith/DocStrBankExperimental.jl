```
ReplicaStrategy{N}
```

Supertype for strategies that can be passed to [`ProjectorMonteCarloProblem`](@ref) and control how many replicas are used, and what information is computed and returned. The number of replicas is `N`.

## Concrete implementations

  * [`NoStats`](@ref): run (possibly one) replica(s), but don't report any additional info.
  * [`AllOverlaps`](@ref): report overlaps between all pairs of replica vectors.

## Interface

A subtype of `ReplicaStrategy{N}` must implement the following function:

  * [`Rimu.replica_stats`](@ref) - return a tuple of `String`s or `Symbols` of names for replica statistics and a tuple of the values. These will be reported to the `DataFrame` returned by [`ProjectorMonteCarloProblem`](@ref).
