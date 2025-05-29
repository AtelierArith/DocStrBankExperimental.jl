```
BinomialPolyaMeta
```

Metadata structure for the BinomialPolya node. It will be passed to rules. In case no meta is provided, the rules will use the means to compute the messages. Both schemes yield very similar results.

# Fields

  * `n_samples::Int`: Number of samples to use for Monte Carlo estimation of the average energy.                   Default is 1, as increasing it adds computational cost without significant benefit.
  * `rng::AbstractRNG`: Random number generator to use for sampling. Defaults to Random.default_rng().
