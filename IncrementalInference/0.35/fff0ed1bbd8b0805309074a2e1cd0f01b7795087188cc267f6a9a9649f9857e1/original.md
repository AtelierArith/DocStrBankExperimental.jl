```julia
mutable struct SolverParams <: DistributedFactorGraphs.AbstractParams
```

Solver parameters for the DistributedFactoGraph.

Dev Notes

  * FIXME change to using kwargs from Parameters.jl
  * TODO remove NothingUnion
  * TODO Upgrade to common @kwargs struct approach
