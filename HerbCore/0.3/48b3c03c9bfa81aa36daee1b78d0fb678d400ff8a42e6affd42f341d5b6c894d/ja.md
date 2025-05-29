```
rulesoftype(node::RuleNode, ruleset::Set{Int}[, ignoreNode::AbstractRuleNode])
rulesoftype(node::RuleNode, rule_index::Int[, ignoreNode::AbstractRuleNode])
```

[`AbstractRuleNode`](@ref) ツリーで使用されているルールセット内のすべてのルールを返しますが、`ignoreNode` サブツリー内のルールは除外されます。

!!! warning
    `ignoreNode` は効果を持つために `node` のサブツリーでなければなりません。

