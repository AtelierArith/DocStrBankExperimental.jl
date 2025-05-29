```
get_executable(rulenode::RuleNode, grammar::Grammar)
```

ルールノード rulenode をルートとする式木で表される実行可能な Julia 式を返します。返された式は eval() を使用して評価できます。
