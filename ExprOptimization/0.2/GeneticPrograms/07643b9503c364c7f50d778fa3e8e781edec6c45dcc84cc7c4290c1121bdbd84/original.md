```
optimize(p::GeneticProgram, grammar::Grammar, typ::Symbol, loss::Function; kwargs...)
```

Expression tree optimization using genetic programming with parameters p, grammar 'grammar', and start symbol typ, and loss function 'loss'.  Loss function has the form: los::Float64=loss(node::RuleNode, grammar::Grammar).
