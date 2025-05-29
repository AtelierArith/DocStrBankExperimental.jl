```julia
struct IMUDeltaFactor{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

Factor type for inertial odometry (preintegration).
