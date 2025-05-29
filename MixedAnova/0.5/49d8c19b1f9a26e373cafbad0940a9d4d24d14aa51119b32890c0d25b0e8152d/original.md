```
canonicalgoodnessoffit(::FixDispDist) = LRT
canonicalgoodnessoffit(::UnivariateDistribution) = FTest

const FixDispDist = Union{Bernoulli, Binomial, Poisson}
```

Return LRT if the distribution has a fixed dispersion.
