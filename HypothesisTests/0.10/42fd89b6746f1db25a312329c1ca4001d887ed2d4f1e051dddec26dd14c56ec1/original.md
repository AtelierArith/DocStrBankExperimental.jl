```
OneSampleADTest(x::AbstractVector{<:Real}, d::UnivariateDistribution)
```

Perform a one-sample Anderson–Darling test of the null hypothesis that the data in vector `x` come from the distribution `d` against the alternative hypothesis that the sample is not drawn from `d`.

Implements: [`pvalue`](@ref)
