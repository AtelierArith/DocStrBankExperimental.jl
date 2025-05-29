```
have_same_shape(node1::AbstractRuleNode, node2::AbstractRuleNode)
```

Returns true iff `node1` and `node2` have the same shape Example: RuleNode(3, [ 	RuleNode(1), 	RuleNode(1) ]) and RuleNode(9, [ 	RuleNode(2), 	Hole(domain) ]) have the same shape: 1 root with 2 children.
