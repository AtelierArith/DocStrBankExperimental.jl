```julia
struct Pose3Pose3Rotation{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

Partial rotation only factor between two Pose3 variables.
