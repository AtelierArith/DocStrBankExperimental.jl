```
max_rulenode_log_probability(rulenode::AbstractRuleNode, grammar::AbstractGrammar)
```

Calculates the highest possible probability within an `AbstractRuleNode`.  That is, for each node and its domain, get the highest probability and multiply it with the probabilities of its children, if present.  As we operate with log probabilities, we sum the logarithms.
