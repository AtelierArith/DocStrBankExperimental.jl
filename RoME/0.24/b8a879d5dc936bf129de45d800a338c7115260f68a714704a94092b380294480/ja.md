```julia
struct Pose2Point2Bearing{B<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

Pose2からPoint2変数への単一次元ベアリング制約。
