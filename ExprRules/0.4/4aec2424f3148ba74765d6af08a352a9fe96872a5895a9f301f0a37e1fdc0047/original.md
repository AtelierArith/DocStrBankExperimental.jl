```
sample(::Type{NodeLoc}, root::RuleNode, typ::Symbol, grammar::Grammar)
```

Selects a uniformly random node in the tree of a given type, specified using its parent such that the subtree can be replaced. Returns a NodeLoc.
