```
rulesoftype(node::RuleNode, grammar::AbstractGrammar, ruletype::Symbol[, ignoreNode::AbstractRuleNode])
```

Returns every rule of nonterminal symbol `ruletype` from the `grammar` that is also used in the [`AbstractRuleNode`](@ref) tree, but not in the `ignoreNode` subtree.

!!! warning
    The `ignoreNode` must be a subtree of `node` for it to have an effect.

