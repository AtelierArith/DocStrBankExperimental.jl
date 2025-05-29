```
sample(::Type{NodeLoc}, root::RuleNode, maxdepth::Int=typemax(Int))
```

Uniformly selects a random node in the tree no deeper than maxdepth using reservoir sampling. Returns a [`NodeLoc`](@ref) that specifies the location using its parent so that the subtree can be replaced.
