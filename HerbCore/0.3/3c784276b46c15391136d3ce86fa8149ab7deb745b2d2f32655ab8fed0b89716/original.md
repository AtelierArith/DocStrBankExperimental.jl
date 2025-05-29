```
get_rulesequence(node::RuleNode, path::Vector{Int})
```

Extract the derivation sequence from a path (sequence of child indices) and an [`AbstractRuleNode`](@ref). If the path is deeper than the deepest node, it returns what it has.
