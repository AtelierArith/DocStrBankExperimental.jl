```
mc_marginal_logp(data, model::PopulationModel, params;
                 repetitions = 20, n_samples = 10^4, rng = Random.default_rng())
```

Estimate the marginal log probability of the data given a model by sampling from the population.
