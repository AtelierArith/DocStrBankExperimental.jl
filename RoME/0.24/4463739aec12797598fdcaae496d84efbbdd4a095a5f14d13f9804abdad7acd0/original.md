```julia
struct PriorPose3ZRP{T1<:(IncrementalInference.SamplableBelief), T2<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractPrior
```

Partial prior belief on Z, Roll, and Pitch of a `Pose3`.
