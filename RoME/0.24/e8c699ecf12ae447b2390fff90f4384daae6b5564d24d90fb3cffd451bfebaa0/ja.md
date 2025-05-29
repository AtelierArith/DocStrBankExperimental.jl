```julia
struct Pose3Pose3{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

2つのPose3準拠変数間の剛体変換因子。
