```
ApproximateMannWhitneyUTest(x::AbstractVector{<:Real}, y::AbstractVector{<:Real})
```

Perform an approximate Mann-Whitney U test of the null hypothesis that the probability that an observation drawn from the same population as `x` is greater than an observation drawn from the same population as `y` is equal to the probability that an observation drawn from the same population as `y` is greater than an observation drawn from the same population as `x` against the alternative hypothesis that these probabilities are not equal.

The p-value is computed using a normal approximation to the distribution of the Mann-Whitney U statistic:

$$
    \begin{align*}
        μ & = \frac{n_x n_y}{2}\\
        σ & = \frac{n_x n_y}{12}\left(n_x + n_y + 1 - \frac{a}{(n_x + n_y)(n_x +
            n_y - 1)}\right)\\
        a & = \sum_{t \in \mathcal{T}} t^3 - t
    \end{align*}
$$

where $\mathcal{T}$ is the set of the counts of tied values at each tied position.

Implements: [`pvalue`](@ref)
