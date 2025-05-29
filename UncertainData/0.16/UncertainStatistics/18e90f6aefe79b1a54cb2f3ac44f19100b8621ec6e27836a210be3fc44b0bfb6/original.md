```
ExactOneSampleKSTestPooled(ud::UncertainDataset,
    d::UnivariateDistribution, n::Int = 1000) -> ExactOneSampleKSTest
```

First, draw `n` realisations of each uncertain value in `ud` and pool them together. Then perform a one-sample exact Kolmogorov–Smirnov test of the null hypothesis that the pooled values comes from the distribution `d` against the alternative hypothesis that the sample is not drawn from `d`.
