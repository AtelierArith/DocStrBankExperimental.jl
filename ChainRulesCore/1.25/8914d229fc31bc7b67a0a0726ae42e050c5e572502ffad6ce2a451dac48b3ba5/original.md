```
rrule_via_ad(::RuleConfig{>:HasReverseMode}, f, args...; kwargs...)
```

This function has the same API as [`rrule`](@ref), but operates via performing reverse mode automatic differentiation. Any `RuleConfig` subtype that supports the [`HasReverseMode`](@ref) special feature must provide an implementation of it.

See also: [`frule_via_ad`](@ref), [`RuleConfig`](@ref) and the documentation on [rule configurations and calling back into AD](@ref config)
