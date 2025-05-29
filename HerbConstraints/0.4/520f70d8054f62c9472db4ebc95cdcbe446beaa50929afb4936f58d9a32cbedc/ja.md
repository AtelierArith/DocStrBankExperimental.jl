```
struct VarNode <: AbstractRuleNode
```

任意の部分木に一致し、それを変数名に割り当てます。`LocalForbidden` 制約は、同一の変数シンボルが異なる木に一致する場合には一致しません。使用例：

```julia
RuleNode(3, [VarNode(:x), VarNode(:x)])
```

これは `RuleNode(3, [RuleNode(1), RuleNode(1)])`、`RuleNode(3, [RuleNode(2), RuleNode(2)])` などに一致しますが、`RuleNode(3, [RuleNode(4, [RuleNode(1)]), RuleNode(4, [RuleNode(1)])])` のようなより大きな部分木にも一致します。
