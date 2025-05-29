```
pattern_match(h1::Union{RuleNode, AbstractHole}, h2::Union{RuleNode, AbstractHole}, vars::Dict{Symbol, AbstractRuleNode})::PatternMatchResult
```

[`Rulenode`](@ref) と/または [`AbstractHole`](@ref) の任意のペアを比較します。いくつかの `AbstractHole` はすでに埋められており、`RuleNode` として扱う必要があることに注意することが重要です。これが、この関数が `(isfilled(h1), isfilled(h2))` に基づいてディスパッチされる理由です。'(RuleNode, AbstractHole)' のケースには、2つの `AbstractHole` 型のノードが含まれる可能性がありますが、そのうちの1つは `rulenode` として扱われるべきです。
