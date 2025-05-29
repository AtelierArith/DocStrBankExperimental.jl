```
ApproximateTwoSampleKSTest(d1::AbstractUncertainValue,
    d2::AbstractUncertainValue, n::Int = 1000) -> ApproximateTwoSampleKSTest
```

Perform an asymptotic two-sample Kolmogorov–Smirnov-test of the null hypothesis that the distribution furnishing the uncertain value `d1` represent the same distribution as the distribution furnishing the uncertain value `d2` against the alternative hypothesis that the furnishing distributions are different.
