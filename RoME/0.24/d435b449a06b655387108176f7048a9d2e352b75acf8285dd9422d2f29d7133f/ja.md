```julia
struct PartialPriorYawPose2{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractPrior
```

Pose2のヨー角のみを制約し、一般的にはジャイロコンパス、磁気計、デュアルGNSSヘディングタイプの測定、またはその他の類似の構造に使用されます。
