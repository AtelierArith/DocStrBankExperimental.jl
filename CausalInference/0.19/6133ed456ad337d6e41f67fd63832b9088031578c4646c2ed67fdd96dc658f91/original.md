```
ges(X; method=:gaussian_bic, penalty=0.5, parallel=false, verbose=false)
```

Compute a causal graph for the given observed data `X` (variables in columns) using GES. Returns the CPDAG, the score improvement relative to the empty graph and time measurements of first and second phase.
