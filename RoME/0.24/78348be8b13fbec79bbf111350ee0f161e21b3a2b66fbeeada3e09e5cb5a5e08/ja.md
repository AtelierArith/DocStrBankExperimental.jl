```julia
struct Pose2Point2{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

Pose2からPoint2変数へのベアリングと範囲の制約。
