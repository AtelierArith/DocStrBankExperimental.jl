```julia
struct RelativeReward{risk} <: DataDrivenLux.AbstractRewardScale{risk}
```

損失をスケールして、最小損失が1になるようにします。
