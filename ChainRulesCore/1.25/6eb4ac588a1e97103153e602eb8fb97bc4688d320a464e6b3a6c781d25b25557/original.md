```
HasReverseMode <: ReverseModeCapability
```

This trait indicates that a `RuleConfig{>:HasReverseMode}` can perform reverse mode AD. If it is set then [`rrule_via_ad`](@ref) must be implemented.
