```
isvariable(grammar::AbstractGrammar, node::RuleNode, mod::Module)::Bool
```

Return true if the rule used by `node` represents a variable.

Taking into account the symbols defined in the given module(s).
