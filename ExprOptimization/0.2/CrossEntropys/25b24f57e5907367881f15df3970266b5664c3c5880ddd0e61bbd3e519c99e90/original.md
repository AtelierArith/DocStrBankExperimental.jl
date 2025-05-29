```
optimize(p::CrossEntropy, grammar::Grammar, typ::Symbol, loss::Function; kwargs...)
```

Expression tree optimization using the cross-entropy method with parameters p, grammar 'grammar', and start symbol typ, and loss function 'loss'.  Loss function has the form: los::Float64=loss(node::RuleNode, grammar::Grammar)

See: Rubinstein, "Optimization of Computer Simulation Models with Rare Events", European Journal of Operations Research, 99, 89-112, 1197
