```
HasForwardsMode <: ForwardsModeCapability
```

This trait indicates that a `RuleConfig{>:HasForwardsMode}` can perform forward mode AD. If it is set then [`frule_via_ad`](@ref) must be implemented.
