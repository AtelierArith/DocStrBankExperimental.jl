```
canonicalgoodnessoffit(::FixDispDist) = LRT
canonicalgoodnessoffit(::UnivariateDistribution) = FTest

const FixDispDist = Union{Bernoulli, Binomial, Poisson}
```

分散が固定されている場合はLRTを返します。
