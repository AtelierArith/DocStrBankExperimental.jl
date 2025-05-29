```julia
struct Pose2Point2Range{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

Pose2からPoint2変数への範囲のみの測定。
