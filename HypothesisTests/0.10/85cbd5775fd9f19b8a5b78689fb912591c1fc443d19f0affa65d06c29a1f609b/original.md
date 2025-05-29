```
ExactOneSampleKSTest(x::AbstractVector{<:Real}, d::UnivariateDistribution)
```

Perform a one-sample exact Kolmogorov–Smirnov test of the null hypothesis that the data in vector `x` comes from the distribution `d` against the alternative hypothesis that the sample is not drawn from `d`.

Implements: [`pvalue`](@ref)
