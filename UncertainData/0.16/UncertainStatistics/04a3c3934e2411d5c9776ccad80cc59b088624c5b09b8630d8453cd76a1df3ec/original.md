```
UnequalVarianceTTest(d1::AbstractUncertainValue, d2::AbstractUncertainValue,
    n::Int = 1000; μ0::Real = 0) -> UnequalVarianceTTest
```

Consider two samples `s1` and `s2`, each consisting of `n` random draws from the distributions furnishing `d1` and `d2`, respectively.

Perform an unequal variance two-sample t-test of the null hypothesis that `s1` and `s2` come from distributions with equal means against the alternative hypothesis that the distributions have different means.
