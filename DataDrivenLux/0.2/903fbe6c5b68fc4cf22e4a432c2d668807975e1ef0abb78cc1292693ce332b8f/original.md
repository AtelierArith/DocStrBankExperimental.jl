```julia
struct RelativeReward{risk} <: DataDrivenLux.AbstractRewardScale{risk}
```

Scales the losses in such a way that the minimum loss is equal to one.
