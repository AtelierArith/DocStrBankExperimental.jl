```
UnequalVarianceZTest(x::AbstractVector{T<:Real}, y::AbstractVector{T<:Real})
```

Perform an unequal variance two-sample z-test of the null hypothesis that `x` and `y` come from distributions with equal means against the alternative hypothesis that the distributions have different means.

Implements: [`pvalue`](@ref), [`confint`](@ref)
