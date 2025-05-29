```
rulesoftype(node::RuleNode, grammar::AbstractGrammar, ruletype::Symbol[, ignoreNode::AbstractRuleNode])
```

非終端シンボル `ruletype` のすべてのルールを `grammar` から返しますが、これは [`AbstractRuleNode`](@ref) ツリーで使用されており、`ignoreNode` サブツリーでは使用されていません。

!!! warning
    `ignoreNode` は効果を持つために `node` のサブツリーでなければなりません。

