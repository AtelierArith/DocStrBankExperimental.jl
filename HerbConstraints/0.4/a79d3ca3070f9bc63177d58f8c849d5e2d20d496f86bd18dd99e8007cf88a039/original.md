```
pattern_match(h1::Union{RuleNode, AbstractHole}, h2::Union{RuleNode, AbstractHole}, vars::Dict{Symbol, AbstractRuleNode})::PatternMatchResult
```

Comparing any pair of [`Rulenode`](@ref) and/or [`AbstractHole`](@ref). It is important to note that some `AbstractHole`s are already filled and should be treated as `RuleNode`. This is why this function is dispatched on `(isfilled(h1), isfilled(h2))`. The '(RuleNode, AbstractHole)' case could still include two nodes of type `AbstractHole`, but one of them should be treated as a rulenode.
