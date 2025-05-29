StochasticPolicy{D, RNG <: AbstractRNG}

Represents a stochastic policy. Action are sampled from an arbitrary distribution.

Constructor:

```
`StochasticPolicy(distribution; rng=Random.default_rng())`
```

# Fields

  * `distribution::D`
  * `rng::RNG` a random number generator
