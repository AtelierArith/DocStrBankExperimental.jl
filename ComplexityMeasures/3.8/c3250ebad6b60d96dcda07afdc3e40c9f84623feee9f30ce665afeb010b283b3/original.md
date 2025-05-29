```
entropy_complexity_curves(c::StatisticalComplexity;
    num_max=1, num_min=1000) -> (min_entropy_complexity, max_entropy_complexity)
```

Calculate the maximum complexity-entropy curve for the statistical complexity according to [Rosso2007](@citet) for `num_max * total_outcomes(c.o)` different values of the normalized information measure of choice (in case of the maximum complexity curves) and `num_min` different values of the normalized information measure of choice (in case of the minimum complexity curve).

This function can also be used to compute the maximum "complexity-extropy curve" if `c.hest` is e.g. [`ShannonExtropy`](@ref), which is the equivalent of the complexity-entropy curves, but using extropy instead of entropy.

## Description

The way the statistical complexity is designed, there is a minimum and maximum possible complexity for data with a given value of an information measure. The calculation time of the maximum complexity curve grows as `O(total_outcomes(c.o)^2)`, and thus takes very long for high numbers of outcomes. This function is inspired by S. Sippels implementation in statcomp [Sippel2016](@cite).

This function will work with any `ProbabilitiesEstimator` where [`total_outcomes`](@ref) is known a priori.
