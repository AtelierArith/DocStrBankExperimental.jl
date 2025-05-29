```
OneSampleZTest(v::AbstractVector{T<:Real}, μ0::Real = 0)
```

Perform a one sample z-test of the null hypothesis that the data in vector `v` comes from a distribution with mean `μ0` against the alternative hypothesis that the distribution does not have mean `μ0`.

Implements: [`pvalue`](@ref), [`confint`](@ref)
