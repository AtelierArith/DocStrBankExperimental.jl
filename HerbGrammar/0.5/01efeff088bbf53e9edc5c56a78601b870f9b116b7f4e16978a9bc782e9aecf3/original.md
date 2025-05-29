```
isterminal(grammar::AbstractGrammar, node::AbstractRuleNode)::Bool
```

Returns true if the production rule used by `node` is terminal, i.e., does not contain any nonterminal symbols.
