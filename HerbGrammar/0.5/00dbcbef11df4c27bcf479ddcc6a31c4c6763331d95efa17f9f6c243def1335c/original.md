```
rulenode2expr(rulenode::AbstractRuleNode, grammar::AbstractGrammar)
```

Converts an [`AbstractRuleNode`](@ref) into a Julia expression corresponding to the rule definitions in the grammar. The returned expression can be evaluated with Julia semantics using `eval()`.
