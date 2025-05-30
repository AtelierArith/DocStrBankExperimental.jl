```
frule_via_ad(::RuleConfig{>:HasForwardsMode}, ȧrgs, f, args...; kwargs...)
```

This function has the same API as [`frule`](@ref), but operates via performing forwards mode automatic differentiation. Any `RuleConfig` subtype that supports the [`HasForwardsMode`](@ref) special feature must provide an implementation of it.

See also: [`rrule_via_ad`](@ref), [`RuleConfig`](@ref) and the documentation on [rule configurations and calling back into AD](@ref config)
