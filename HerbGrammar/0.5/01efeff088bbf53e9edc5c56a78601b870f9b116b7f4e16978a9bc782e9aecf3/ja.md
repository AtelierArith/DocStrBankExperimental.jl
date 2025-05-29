```
isterminal(grammar::AbstractGrammar, node::AbstractRuleNode)::Bool
```

`node`によって使用される生成規則が終端である場合、すなわち非終端記号を含まない場合にtrueを返します。
