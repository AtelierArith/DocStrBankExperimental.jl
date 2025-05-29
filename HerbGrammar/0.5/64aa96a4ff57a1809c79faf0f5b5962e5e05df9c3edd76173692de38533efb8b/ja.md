```
iscomplete(grammar::AbstractGrammar, node::RuleNode)
```

[`RuleNode`](@ref)によって表される式が完全な式である場合、すなわち完全に定義されていて、[`Hole`](@ref)を持たない場合にtrueを返します。
