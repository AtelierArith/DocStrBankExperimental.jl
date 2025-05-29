```
have_same_shape(node1::AbstractRuleNode, node2::AbstractRuleNode)
```

`node1` と `node2` が同じ形状を持つ場合に true を返します。例: RuleNode(3, [ 	RuleNode(1), 	RuleNode(1) ]) と RuleNode(9, [ 	RuleNode(2), 	Hole(domain) ]) は同じ形状を持ちます: 1 つのルートと 2 つの子。
