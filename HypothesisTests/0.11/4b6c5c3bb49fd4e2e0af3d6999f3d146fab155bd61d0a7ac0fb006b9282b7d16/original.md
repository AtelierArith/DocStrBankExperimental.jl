```
MannWhitneyUTest(x::AbstractVector{<:Real}, y::AbstractVector{<:Real})
```

Perform a Mann-Whitney U test of the null hypothesis that the probability that an observation drawn from the same population as `x` is greater than an observation drawn from the same population as `y` is equal to the probability that an observation drawn from the same population as `y` is greater than an observation drawn from the same population as `x` against the alternative hypothesis that these probabilities are not equal.

The Mann-Whitney U test is sometimes known as the Wilcoxon rank-sum test.

When there are no tied ranks and ≤50 samples, or tied ranks and ≤10 samples, `MannWhitneyUTest` performs an exact Mann-Whitney U test. In all other cases, `MannWhitneyUTest` performs an approximate Mann-Whitney U test. Behavior may be further controlled by using [`ExactMannWhitneyUTest`](@ref) or [`ApproximateMannWhitneyUTest`](@ref) directly.

Implements: [`pvalue`](@ref)
