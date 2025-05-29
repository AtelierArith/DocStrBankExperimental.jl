```
EqualVarianceTTestElementWise(d1::UncertainDataset, d2::UncertainDataset,
    n::Int = 1000; μ0::Real = 0) -> Vector{EqualVarianceTTest}
```

Consider two samples `s1[i]` and `s2[i]`, each consisting of `n` random draws from the distributions furnishing the uncertain values `d1[i]` and `d2[i]`, respectively. This function performs an elementwise `EqualVarianceTTest` on the pairs `(s1[i], s2[i])`. Specifically:

Performs an pairwise two-sample t-test of the null hypothesis that `s1[i]` and `s2[i]` come from distributions with equal means and variances against the alternative hypothesis that the distributions have different means but equal variances.
