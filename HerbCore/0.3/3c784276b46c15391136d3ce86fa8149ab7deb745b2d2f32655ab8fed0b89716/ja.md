```
get_rulesequence(node::RuleNode, path::Vector{Int})
```

パス（子インデックスのシーケンス）と[`AbstractRuleNode`](@ref)から導出シーケンスを抽出します。パスが最も深いノードよりも深い場合、持っているものを返します。
