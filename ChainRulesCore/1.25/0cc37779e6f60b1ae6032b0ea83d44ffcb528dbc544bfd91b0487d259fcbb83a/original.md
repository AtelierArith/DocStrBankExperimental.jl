```
NoForwardsMode <: ForwardsModeCapability
```

This is the complement to [`HasForwardsMode`](@ref). To avoid ambiguities [`RuleConfig`]s that do not support performing forwards mode AD should be `RuleConfig{>:NoForwardsMode}`.
