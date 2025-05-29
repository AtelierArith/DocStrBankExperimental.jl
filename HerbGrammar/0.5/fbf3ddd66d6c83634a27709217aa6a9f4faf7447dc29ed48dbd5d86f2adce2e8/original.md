```
contains_returntype(node::RuleNode, grammar::AbstractGrammar, sym::Symbol, maxdepth::Int=typemax(Int))
```

Returns true if the tree rooted at `node` contains at least one node at depth less than `maxdepth` with the given return type or nonterminal symbol.
