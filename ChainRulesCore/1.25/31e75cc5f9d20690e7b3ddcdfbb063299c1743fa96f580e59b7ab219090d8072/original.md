```
RuleConfig{T}
```

The configuration for what rules to use. `T`: **traits**. This should be a `Union` of all special traits needed for rules to be allowed to be defined for your AD. If nothing special this should be set to `Union{}`.

**AD authors** should define a subtype of `RuleConfig` to use when calling `frule`/`rrule`.

**Rule authors** can dispatch on this config when defining rules. For example:

```julia
# only define rrule for `pop!` on AD systems where mutation is supported.
rrule(::RuleConfig{>:SupportsMutation}, typeof(pop!), ::Vector) = ...

# this definition of map is for any AD that defines a forwards mode
rrule(conf::RuleConfig{>:HasForwardsMode}, typeof(map), ::Vector) = ...

# this definition of map is for any AD that only defines a reverse mode.
# It is not as good as the rrule that can be used if the AD defines a forward-mode as well.
rrule(conf::RuleConfig{>:Union{NoForwardsMode, HasReverseMode}}, typeof(map), ::Vector) = ...
```

For more details see [rule configurations and calling back into AD](@ref config).
