```
pattern_match(rns::Vector{AbstractRuleNode}, mns::Vector{AbstractRuleNode}, vars::Dict{Symbol, AbstractRuleNode})::PatternMatchResult
```

Pairwiseは、2つの順序付きリストの[AbstractRuleNode](@ref)sを一致させようとします。通常、この関数は2つのAbstractRuleNodeの子をパターンマッチするために使用されます。
