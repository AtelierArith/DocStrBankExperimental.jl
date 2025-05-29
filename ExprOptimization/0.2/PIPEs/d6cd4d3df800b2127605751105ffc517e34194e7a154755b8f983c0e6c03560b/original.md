```
optimize(p::PIPE, grammar::Grammar, typ::Symbol, loss::Function; kwargs...)
```

Expression tree optimization using the PIPE algorithm with parameters p, grammar 'grammar', start symbol typ, and loss function 'loss'.  Loss function has the form: los::Float64=loss(node::RuleNode, grammar::Grammar).
