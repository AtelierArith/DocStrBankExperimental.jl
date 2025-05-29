```
SignedRankTest(x::AbstractVector{<:Real})
SignedRankTest(x::AbstractVector{<:Real}, y::AbstractVector{<:Real})
```

Perform a Wilcoxon signed rank test of the null hypothesis that the distribution of `x` (or the difference `x - y` if `y` is provided) has zero median against the alternative hypothesis that the median is non-zero.

When there are no tied ranks and ≤50 samples, or tied ranks and ≤15 samples, `SignedRankTest` performs an exact signed rank test. In all other cases, `SignedRankTest` performs an approximate signed rank test. Behavior may be further controlled by using [`ExactSignedRankTest`](@ref) or [`ApproximateSignedRankTest`](@ref) directly.

Implements: [`pvalue`](@ref), [`confint`](@ref)
