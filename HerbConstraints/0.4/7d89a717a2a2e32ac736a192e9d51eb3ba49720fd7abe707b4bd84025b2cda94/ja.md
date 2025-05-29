```
substitute!(solver::GenericSolver, path::Vector{Int}, new_node::AbstractRuleNode; is_domain_increasing::Union{Nothing, Bool}=nothing)
```

`path`のノードを`new_node`で置き換えます。

  * `is_domain_increasing`: すべての文法制約を根本から再伝播する必要があるかどうかを示します。

ドメイン増加置換は、ドメインから値を繰り返し削除することでは達成できない置換です。ドメイン増加イベントの例: `hole[{3, 4, 5}] -> hole[{1, 2}]`。ドメイン減少イベントの例: `hole[{3, 4, 5}] -> rulenode(4, [hole[{1, 2}], rulenode(1)])`。
