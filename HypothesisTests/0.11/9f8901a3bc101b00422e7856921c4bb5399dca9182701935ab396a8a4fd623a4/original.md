```
OneSampleZTest(xbar::Real, stddev::Real, n::Int, μ0::Real = 0)
```

Perform a one sample z-test of the null hypothesis that `n` values with mean `xbar` and population standard deviation `stddev`  come from a distribution with mean `μ0` against the alternative hypothesis that the distribution does not have mean `μ0`.

Implements: [`pvalue`](@ref), [`confint`](@ref)
