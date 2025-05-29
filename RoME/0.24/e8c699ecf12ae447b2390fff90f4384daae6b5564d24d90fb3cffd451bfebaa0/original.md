```julia
struct Pose3Pose3{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

Rigid transform factor between two Pose3 compliant variables.
