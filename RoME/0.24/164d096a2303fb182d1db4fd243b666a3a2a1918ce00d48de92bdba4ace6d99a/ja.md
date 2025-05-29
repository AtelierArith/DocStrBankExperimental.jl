```julia
struct Pose3Pose3Rotation{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

2つのPose3変数間の部分回転のみの因子。
