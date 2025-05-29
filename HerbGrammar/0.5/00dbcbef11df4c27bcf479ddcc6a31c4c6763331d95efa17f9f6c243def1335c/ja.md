```
rulenode2expr(rulenode::AbstractRuleNode, grammar::AbstractGrammar)
```

[`AbstractRuleNode`](@ref)を文法のルール定義に対応するJulia式に変換します。返された式は、`eval()`を使用してJuliaのセマンティクスで評価できます。
