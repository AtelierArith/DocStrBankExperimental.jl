```
OrderStatistic{D<:UnivariateDistribution,S<:ValueSupport} <: UnivariateDistribution{S}
```

The distribution of an order statistic from IID samples from a univariate distribution.

```
OrderStatistic(dist::UnivariateDistribution, n::Int, rank::Int; check_args::Bool=true)
```

Construct the distribution of the `rank` $=i$th order statistic from `n` independent samples from `dist`.

The $i$th order statistic of a sample is the $i$th element of the sorted sample. For example, the 1st order statistic is the sample minimum, while the $n$th order statistic is the sample maximum.

If $f$ is the probability density (mass) function of `dist` with distribution function $F$, then the probability density function $g$ of the order statistic for continuous `dist` is

$$
g(x; n, i) = {n \choose i} [F(x)]^{i-1} [1 - F(x)]^{n-i} f(x),
$$

and the probability mass function $g$ of the order statistic for discrete `dist` is

$$
g(x; n, i) = \sum_{k=i}^n {n \choose k} \left( [F(x)]^k [1 - F(x)]^{n-k} - [F(x_-)]^k [1 - F(x_-)]^{n-k} \right),
$$

where $x_-$ is the largest element in the support of `dist` less than $x$.

For the joint distribution of a subset of order statistics, use [`JointOrderStatistics`](@ref) instead.

## Examples

```julia
OrderStatistic(Cauchy(), 10, 1)              # distribution of the sample minimum
OrderStatistic(DiscreteUniform(10), 10, 10)  # distribution of the sample maximum
OrderStatistic(Gamma(1, 1), 11, 5)           # distribution of the sample median
```
