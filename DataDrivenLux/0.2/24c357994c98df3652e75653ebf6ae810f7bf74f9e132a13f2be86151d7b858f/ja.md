```julia
struct AbsoluteReward{risk} <: DataDrivenLux.AbstractRewardScale{risk}
```

損失をスケーリングし、最小の損失が最も影響力のある報酬となるようにします。
