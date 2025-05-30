```
NoReverseMode <: ReverseModeCapability
```

This is the complement to [`HasReverseMode`](@ref). To avoid ambiguities [`RuleConfig`]s that do not support performing reverse mode AD should be `RuleConfig{>:NoReverseMode}`.
