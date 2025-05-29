```
StatsBase.sample(::Type{NodeLoc}, root::RuleNode, typ::Symbol, grammar::AbstractGrammar, maxdepth::Int=typemax(Int))
```

Uniformly selects a random node in the tree of a given type, specified using its parent such that the subtree can be replaced. Returns a [`NodeLoc`](@ref).
