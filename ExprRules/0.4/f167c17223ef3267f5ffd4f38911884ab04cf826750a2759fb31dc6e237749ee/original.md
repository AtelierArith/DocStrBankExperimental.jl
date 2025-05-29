```
sample(::Type{NodeLoc}, root::RuleNode, maxdepth::Int=typemax(Int))
```

Selects a uniformly random node in the tree no deeper than maxdepth using reservoir sampling. Returns a NodeLoc that specifies the location using its parent so that the subtree can be replaced.
