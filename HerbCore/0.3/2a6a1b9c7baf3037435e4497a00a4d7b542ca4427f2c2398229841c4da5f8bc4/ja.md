```
contains_hole(rn::RuleNode) = any(contains_hole(c) for c ∈ rn.children)
```

[`AbstractRuleNode`](@ref) ツリーが [`AbstractHole`](@ref) を含むかどうかをチェックします。
