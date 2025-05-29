```
optimize(p::MonteCarlo, grammar::Grammar, typ::Symbol, loss::Function; kwargs...)

Expression tree optimization using Monte Carlo with parameters p, grammar 'grammar', start symbol typ, and loss function 'loss'.  Loss function has the form: los::Float64=loss(node::RuleNode, grammar::Grammar).
```
