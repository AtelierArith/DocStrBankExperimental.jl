```
ExactOneSampleKSTest(uv::AbstractUncertainValue,
    d::UnivariateDistribution, n::Int = 1000) -> ExactOneSampleKSTest
```

Perform a one-sample exact Kolmogorov–Smirnov test of the null hypothesis that a draw of `n` realisations of the uncertain value `uv` comes from the distribution `d` against the alternative hypothesis that the sample is not drawn from `d`.
