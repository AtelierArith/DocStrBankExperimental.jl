```
derivation_heuristic(iter::MLFSIterator, domain::Vector{Int})
```

Defines `derivation_heuristic` for the iterator type `MLFSIterator`.  Sorts the indices within a domain, that is grammar rules, by decreasing log_probabilities. 

This will invert the enumeration order if probabilities are equal.
