```julia
struct AbsoluteReward{risk} <: DataDrivenLux.AbstractRewardScale{risk}
```

Scales the losses in such a way that the minimum loss is the most influential reward.
