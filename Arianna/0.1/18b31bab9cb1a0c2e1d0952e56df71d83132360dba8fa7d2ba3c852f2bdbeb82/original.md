```
abstract type Policy
```

Abstract type representing proposal policies for Monte Carlo actions.

A Policy defines how actions are sampled and their proposal probabilities are calculated. Concrete subtypes work together with specific Action types to implement the proposal mechanism.
