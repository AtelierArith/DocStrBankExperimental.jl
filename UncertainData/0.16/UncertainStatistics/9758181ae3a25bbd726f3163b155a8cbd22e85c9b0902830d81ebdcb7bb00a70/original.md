```
UnequalVarianceTTestPooled(d1::UncertainDataset, d2::UncertainDataset,
    n::Int = 1000; μ0::Real = 0) -> UnequalVarianceTTest
```

Consider two samples `s1[i]` and `s2[i]`, each consisting of `n` random draws from the distributions furnishing the uncertain values `d1[i]` and `d2[i]`, respectively. Gather all `s1[i]` in a pooled sample `S1`, and all `s2[i]` in a pooled sample `S2`.

This function performs an unequal variance two-sample t-test of the null hypothesis that `S1` and `S2` come from distributions with equal means against the alternative hypothesis that the distributions have different means.
