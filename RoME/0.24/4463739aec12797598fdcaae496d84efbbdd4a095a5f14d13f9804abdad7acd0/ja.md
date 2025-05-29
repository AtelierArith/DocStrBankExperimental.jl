```julia
struct PriorPose3ZRP{T1<:(IncrementalInference.SamplableBelief), T2<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractPrior
```

`Pose3`のZ、ロール、ピッチに関する部分的な事前信念。
