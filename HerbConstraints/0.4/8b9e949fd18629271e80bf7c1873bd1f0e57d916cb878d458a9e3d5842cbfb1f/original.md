```
pattern_match(rns::Vector{AbstractRuleNode}, mns::Vector{AbstractRuleNode}, vars::Dict{Symbol, AbstractRuleNode})::PatternMatchResult
```

Pairwise tries to match two ordered lists of [AbstractRuleNode](@ref)s.  Typically, this function is used to pattern match the children two AbstractRuleNodes.
