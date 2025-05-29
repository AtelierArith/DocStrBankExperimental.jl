```
sample([rng], d::Parameterized, [n_draws])
```

Draws `n_draws` samples from the parameter distributions `d`. Returns an array, with  parameters as columns. `rng` is optional and defaults to `Random.GLOBAL_RNG`. `n_draws` is  optional and defaults to 1. Performed in computational space.
