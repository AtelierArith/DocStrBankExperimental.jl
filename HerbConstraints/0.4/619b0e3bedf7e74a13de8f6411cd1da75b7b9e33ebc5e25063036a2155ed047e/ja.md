```
pattern_match(rn::AbstractRuleNode, mn::AbstractRuleNode)::PatternMatchResult
```

再帰的に [`AbstractRuleNode`](@ref) `rn` を [`AbstractRuleNode`](@ref) `mn` と一致させようとします。一致したかどうかを示す `PatternMatchResult` を返します。
