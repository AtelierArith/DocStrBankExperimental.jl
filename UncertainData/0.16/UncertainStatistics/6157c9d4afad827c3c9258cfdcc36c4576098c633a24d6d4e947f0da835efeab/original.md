```
UnequalVarianceTTestElementWise(d1::UncertainDataset, d2::UncertainDataset,
    n::Int = 1000; μ0::Real = 0) -> Vector{UnequalVarianceTTest}
```

Consider two samples `s1[i]` and `s2[i]`, each consisting of `n` random draws from the distributions furnishing the uncertain values `d1[i]` and `d2[i]`, respectively. This function performs an elementwise `EqualVarianceTTest` on the pairs `(s1[i], s2[i])`. Specifically:

Performs an pairwise unequal variance two-sample t-test of the null hypothesis that `s1[i]` and `s2[i]` come from distributions with equal means against the alternative hypothesis that the distributions have different means.

This test is sometimes known as Welch's t-test. It differs from the equal variance t-test in that it computes the number of degrees of freedom of the test using the Welch-Satterthwaite equation:

$$
    ν_{χ'} ≈ \frac{\left(\sum_{i=1}^n k_i s_i^2\right)^2}{\sum_{i=1}^n
        \frac{(k_i s_i^2)^2}{ν_i}}
$$
