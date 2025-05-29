```
optimize(p::ExprOptAlgorithm, grammar::Grammar, typ::Symbol, loss::Function; kwargs...)
```

Main entry for expression optimization.  Use concrete ExprOptAlgorithm to specify optimization algorithm. Optimize using grammar and start symbol, typ, and loss function.  Loss function has the form: los::Float64=loss(node::RuleNode).
