```
OneSampleADTest(uv::UncertainValue, d::UnivariateDistribution,
    n::Int = 1000) -> OneSampleADTest
```

Perform a one-sample Anderson–Darling test of the null hypothesis that a draw of `n` realisations of the uncertain value `uv` comes from the distribution `d` against the alternative hypothesis that the sample is not drawn from `d`.
