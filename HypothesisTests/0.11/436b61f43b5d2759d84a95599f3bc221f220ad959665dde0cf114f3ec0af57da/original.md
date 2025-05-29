```
ApproximateOneSampleKSTest(x::AbstractVector{<:Real}, d::UnivariateDistribution)
```

Perform an asymptotic one-sample Kolmogorov–Smirnov test of the null hypothesis that the data in vector `x` comes from the distribution `d` against the alternative hypothesis that the sample is not drawn from `d`.

Implements: [`pvalue`](@ref)
