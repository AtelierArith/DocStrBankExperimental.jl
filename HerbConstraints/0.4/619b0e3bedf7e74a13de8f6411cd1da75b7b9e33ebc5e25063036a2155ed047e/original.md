```
pattern_match(rn::AbstractRuleNode, mn::AbstractRuleNode)::PatternMatchResult
```

Recursively tries to match [`AbstractRuleNode`](@ref) `rn` with [`AbstractRuleNode`](@ref) `mn`. Returns a `PatternMatchResult` that describes if the pattern was matched.
