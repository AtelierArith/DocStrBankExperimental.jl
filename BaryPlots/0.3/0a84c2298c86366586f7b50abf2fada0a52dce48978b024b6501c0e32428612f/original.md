```
struct ReplicatorParams
```

Holds parameters for the replicator dynamics, including payoff functions and extra parameters.

# Fields

  * `payoff_functions`: A tuple of three payoff functions `(payoff1, payoff2, payoff3)`, one for each strategy.
  * `extra_params`: A `NamedTuple` containing additional parameters required by the payoff functions.
