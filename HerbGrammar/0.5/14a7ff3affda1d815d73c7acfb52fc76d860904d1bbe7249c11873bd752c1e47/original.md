```
remove_rule!(g::AbstractGrammar, idx::Int)
```

Removes the rule corresponding to `idx` from the grammar.  In order to avoid shifting indices, the rule is replaced with `nothing`, and all other data structures are updated accordingly.
