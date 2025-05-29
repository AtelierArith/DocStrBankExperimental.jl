```
StatsBase.sample(::Type{NodeLoc}, root::RuleNode, typ::Symbol, grammar::AbstractGrammar, maxdepth::Int=typemax(Int))
```

指定された親を使用して、置き換え可能な部分木を持つ特定のタイプのツリー内のランダムなノードを均等に選択します。 [`NodeLoc`](@ref) を返します。
