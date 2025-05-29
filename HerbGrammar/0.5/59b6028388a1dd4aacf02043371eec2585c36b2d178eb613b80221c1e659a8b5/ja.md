```
isterminal(grammar::AbstractGrammar, rule_index::Int)::Bool
```

`rule_index`の生成規則が終端である場合、すなわち非終端記号を含まない場合はtrueを返します。
