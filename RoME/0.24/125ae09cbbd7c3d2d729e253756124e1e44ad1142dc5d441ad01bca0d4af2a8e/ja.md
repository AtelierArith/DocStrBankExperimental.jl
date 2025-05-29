```julia
mutable struct Pose2Point2BearingRange{B<:(IncrementalInference.SamplableBelief), R<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

Pose2からPoint2変数へのベアリングと範囲の制約。
