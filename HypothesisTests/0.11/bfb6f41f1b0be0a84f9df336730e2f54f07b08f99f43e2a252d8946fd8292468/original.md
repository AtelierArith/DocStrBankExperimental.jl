```
ApproximateSignedRankTest(x::AbstractVector{<:Real}[, y::AbstractVector{<:Real}])
```

Perform a Wilcoxon approximate signed rank U test of the null hypothesis that the distribution of `x` (or the difference `x - y` if `y` is provided) has zero median against the alternative hypothesis that the median is non-zero.

The p-value is computed using a normal approximation to the distribution of the signed rank statistic:

$$
    \begin{align*}
        μ & = \frac{n(n + 1)}{4}\\
        σ & = \frac{n(n + 1)(2 * n + 1)}{24} - \frac{a}{48}\\
        a & = \sum_{t \in \mathcal{T}} t^3 - t
    \end{align*}
$$

where $\mathcal{T}$ is the set of the counts of tied values at each tied position.

Implements: [`pvalue`](@ref), [`confint`](@ref)
