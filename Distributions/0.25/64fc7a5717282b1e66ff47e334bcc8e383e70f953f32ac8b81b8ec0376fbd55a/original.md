```
JointOrderStatistics <: ContinuousMultivariateDistribution
```

The joint distribution of a subset of order statistics from a sample from a continuous univariate distribution.

```
JointOrderStatistics(
    dist::ContinuousUnivariateDistribution,
    n::Int,
    ranks=Base.OneTo(n);
    check_args::Bool=true,
)
```

Construct the joint distribution of order statistics for the specified `ranks` from an IID sample of size `n` from `dist`.

The $i$th order statistic of a sample is the $i$th element of the sorted sample. For example, the 1st order statistic is the sample minimum, while the $n$th order statistic is the sample maximum.

`ranks` must be a sorted vector or tuple of unique `Int`s between 1 and `n`.

For a single order statistic, use [`OrderStatistic`](@ref) instead.

## Examples

```julia
JointOrderStatistics(Normal(), 10)           # Product(fill(Normal(), 10)) restricted to ordered vectors
JointOrderStatistics(Cauchy(), 10, 2:9)      # joint distribution of all but the extrema
JointOrderStatistics(Cauchy(), 10, (1, 10))  # joint distribution of only the extrema
```
