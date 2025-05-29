```
EqualVarianceZTest(x::AbstractVector{T<:Real}, y::AbstractVector{T<:Real})
```

Perform a two-sample z-test of the null hypothesis that `x` and `y` come from distributions with equal means and variances against the alternative hypothesis that the distributions have different means but equal variances.

Implements: [`pvalue`](@ref), [`confint`](@ref)
