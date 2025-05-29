```julia
mutable struct Pose2Point2BearingRange{B<:(IncrementalInference.SamplableBelief), R<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

Bearing and Range constraint from a Pose2 to Point2 variable.
