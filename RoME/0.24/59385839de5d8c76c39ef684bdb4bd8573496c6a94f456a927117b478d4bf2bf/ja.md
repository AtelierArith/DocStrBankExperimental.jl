```julia
mutable struct MutablePose2Pose2Gaussian <: DistributedFactorGraphs.AbstractManifoldMinimize
```

特化されたPose2Pose2因子タイプ（ガウス型）で、因子グラフのブランチとしてオドメトリ情報を迅速に蓄積することを可能にします。
