```
ExactMannWhitneyUTest(x::AbstractVector{<:Real}, y::AbstractVector{<:Real})
```

Perform an exact Mann-Whitney U test of the null hypothesis that the probability that an observation drawn from the same population as `x` is greater than an observation drawn from the same population as `y` is equal to the probability that an observation drawn from the same population as `y` is greater than an observation drawn from the same population as `x` against the alternative hypothesis that these probabilities are not equal.

When there are no tied ranks, the exact p-value is computed using the `wilcoxcdf` and `wilcoxccdf` functions from the `StatsFuns` package. In the presence of tied ranks, a p-value is computed by exhaustive enumeration of permutations, which can be very slow for even moderately sized data sets.

Implements: [`pvalue`](@ref)
