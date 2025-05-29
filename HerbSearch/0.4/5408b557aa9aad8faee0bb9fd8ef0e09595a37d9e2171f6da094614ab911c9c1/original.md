```
sample(root::RuleNode, typ::Symbol, grammar::AbstractGrammar,
                      maxdepth::Int=typemax(Int))
```

Uniformly selects a random node of the given return type typ limited by maxdepth.
