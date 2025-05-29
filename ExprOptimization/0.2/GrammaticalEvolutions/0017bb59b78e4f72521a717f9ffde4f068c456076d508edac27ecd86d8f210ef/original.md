```
optimize(p::GrammaticalEvolution, grammar::Grammar, typ::Symbol, loss::Function; kwargs...)
```

Grammatical Evolution algorithm with parameters p, grammar 'grammar', start symbol typ, and loss function 'loss'.  Loss function has the form: los::Float64=loss(node::RuleNode, grammar::Grammar).

See: Ryan, Collins, O'Neil, "Grammatical Evolution: Evolving Programs for an Arbitrary Language",      in European Conference on Genetic Programming, Spring, 1998, pp. 83-96. 
