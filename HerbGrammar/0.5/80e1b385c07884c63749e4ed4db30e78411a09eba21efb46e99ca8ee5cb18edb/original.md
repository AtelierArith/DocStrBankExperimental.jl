```
normalize!(grammar::ContextSensitiveGrammar, type::Union{Symbol, Nothing}=nothing)
```

A function for normalizing the probabilities of a probabilistic [`ContextSensitiveGrammar`](@ref). If the optional `type` argument is provided, only the rules of that type are normalized.  If the grammar is not probabilistic, i.e. `grammar.log_probabilities==nothing`, a uniform distribution is initialized.
