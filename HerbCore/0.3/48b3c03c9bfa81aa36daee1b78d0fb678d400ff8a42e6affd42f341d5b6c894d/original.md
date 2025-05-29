```
rulesoftype(node::RuleNode, ruleset::Set{Int}[, ignoreNode::AbstractRuleNode])
rulesoftype(node::RuleNode, rule_index::Int[, ignoreNode::AbstractRuleNode])
```

Returns every rule in the ruleset that is also used in the [`AbstractRuleNode`](@ref) tree, but not in the `ignoreNode` subtree.

!!! warning
    The `ignoreNode` must be a subtree of `node` for it to have an effect.

