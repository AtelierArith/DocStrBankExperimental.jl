```
log_probability(grammar::AbstractGrammar, index::Int)::Real
```

Returns the log probability for the rule at `index` in the grammar.

!!! warning
    If the grammar is not probabilistic, a warning is displayed, and a uniform probability is assumed.

