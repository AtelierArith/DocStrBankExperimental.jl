```julia
struct IMUDeltaFactor{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

慣性オドメトリ（前統合）のためのファクタータイプ。
