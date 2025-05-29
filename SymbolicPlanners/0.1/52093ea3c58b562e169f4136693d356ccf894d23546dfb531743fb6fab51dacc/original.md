```
FunctionalVPolicy(evaluator, domain, spec)
```

Policy solution where state values are defined by an `evaluator`, a one-argument function that outputs a value estimate for each `state`. The domain and specification also have to be provided, so that the policy knows how to derive action Q-values for each state.
