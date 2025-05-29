```julia
struct Pose2 <: DistributedFactorGraphs.InferenceVariable
```

Pose2は、一般的な2D SLAMに使用される2つのユークリッド変換と1つの円形回転のSE(2)メカニズムです。
