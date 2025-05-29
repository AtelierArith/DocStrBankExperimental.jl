```
struct DomainRuleNode <: AbstractRuleNode
```

そのドメイン内の任意の1つのルールに一致します。使用例：

```
DomainRuleNode(Bitvector((0, 0, 1, 1)), [RuleNode(1), RuleNode(1)])
```

これは `RuleNode(3, [RuleNode(1), RuleNode(1)])` と `RuleNode(4, [RuleNode(1), RuleNode(1)])` と `UniformHole({3, 4}, [RuleNode(1), RuleNode(1)])` に一致します。
