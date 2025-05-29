```
struct VarNode <: AbstractRuleNode
```

Matches any subtree and assigns it to a variable name. The `LocalForbidden` constraint will not match if identical variable symbols match to different trees. Example usage:

```julia
RuleNode(3, [VarNode(:x), VarNode(:x)])
```

This matches `RuleNode(3, [RuleNode(1), RuleNode(1)])`, `RuleNode(3, [RuleNode(2), RuleNode(2)])`, etc. but also larger subtrees such as `RuleNode(3, [RuleNode(4, [RuleNode(1)]), RuleNode(4, [RuleNode(1)])])`
