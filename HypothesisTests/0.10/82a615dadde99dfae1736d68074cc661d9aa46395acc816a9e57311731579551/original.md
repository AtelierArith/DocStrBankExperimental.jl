```
UnequalVarianceTTest(x::AbstractVector{T<:Real}, y::AbstractVector{T<:Real})
```

Perform an unequal variance two-sample t-test of the null hypothesis that `x` and `y` come from distributions with equal means against the alternative hypothesis that the distributions have different means.

This test is sometimes known as Welch's t-test. It differs from the equal variance t-test in that it computes the number of degrees of freedom of the test using the Welch-Satterthwaite equation:

$$
    ν_{χ'} ≈ \frac{\left(\sum_{i=1}^n k_i s_i^2\right)^2}{\sum_{i=1}^n
        \frac{(k_i s_i^2)^2}{ν_i}}
$$

Implements: [`pvalue`](@ref), [`confint`](@ref)
