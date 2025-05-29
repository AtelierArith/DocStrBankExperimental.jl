```
sample(root::RuleNode, typ::Symbol, grammar::Grammar,
                      maxdepth::Int=typemax(Int))
```

Selects a uniformly random node of the given return type, typ, limited to maxdepth.
