```
probability(grammar::AbstractGrammar, index::Int)::Real
```

Return the probability for a rule in the grammar. Use [`log_probability`](@ref) whenever possible.

!!! warning
    If the grammar is not probabilistic, a warning is displayed, and a uniform probability is assumed.

