```
ExactSignedRankTest(x::AbstractVector{<:Real}[, y::AbstractVector{<:Real}])
```

Perform a Wilcoxon exact signed rank U test of the null hypothesis that the distribution of `x` (or the difference `x - y` if `y` is provided) has zero median against the alternative hypothesis that the median is non-zero.

When there are no tied ranks, the exact p-value is computed using the `signrankcdf` and `signrankccdf` functions from the `StatsFuns` package. In the presence of tied ranks, a p-value is computed by exhaustive enumeration of permutations, which can be very slow for even moderately sized data sets.

Implements: [`pvalue`](@ref), [`confint`](@ref)
