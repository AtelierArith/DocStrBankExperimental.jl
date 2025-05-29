```
pyhf_loglikelihoodof(expected, obs)
```

Return a callable Function `L(αs)` that would calculate the log likelihood. `expected` is a callable of `αs` as well.

!!! note
    The so called "constraint" terms (from priors) are NOT included here.

