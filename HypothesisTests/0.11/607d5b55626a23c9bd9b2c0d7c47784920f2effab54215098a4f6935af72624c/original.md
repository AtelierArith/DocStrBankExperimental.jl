```
PowerDivergenceTest(x[, y]; lambda = 1.0, theta0 = ones(length(x))/length(x))
```

Perform a Power Divergence test.

If `y` is not given and `x` is a matrix with one row or column, or `x` is a vector, then a goodness-of-fit test is performed (`x` is treated as a one-dimensional contingency table). In this case, the hypothesis tested is whether the population probabilities equal those in `theta0`, or are all equal if `theta0` is not given.

If `x` is a matrix with at least two rows and columns, it is taken as a two-dimensional contingency table. Otherwise, `x` and `y` must be vectors of the same length. The contingency table is calculated using the `counts` function from the `StatsBase` package. Then the power divergence test is conducted under the null hypothesis that the joint distribution of the cell counts in a 2-dimensional contingency table is the product of the row and column marginals.

Note that the entries of `x` (and `y` if provided) must be non-negative integers.

Computed confidence intervals by default are Quesenberry-Hurst intervals if the minimum of the expected cell counts exceeds 100, and Sison-Glaz intervals otherwise. See the [`confint(::PowerDivergenceTest)`](@ref) documentation for a list of supported methods to compute confidence intervals.

The power divergence test is given by

$$
    \dfrac{2}{λ(λ+1)}\sum_{i=1}^I \sum_{j=1}^J n_{ij} \left[(n_{ij}
    /\hat{n}_{ij})^λ -1\right]
$$

where $n_{ij}$ is the cell count in the $i$ th row and $j$ th column and $λ$ is a real number determining the nature of the test to be performed:

  * $λ = 1$: equal to Pearson's chi-squared statistic
  * $λ \to 0$: converges to the likelihood ratio test statistic
  * $λ \to -1$: converges to the minimum discrimination information statistic (Gokhale and Kullback, 1978)
  * $λ = -2$: equals Neyman modified chi-squared (Neyman, 1949)
  * $λ = -1/2$: equals the Freeman-Tukey statistic (Freeman and Tukey, 1950).

Under regularity conditions, the asymptotic distributions are identical (see Drost et. al. 1989). The $χ^2$ null approximation works best for $λ$ near $2/3$.

Implements: [`pvalue`](@ref), [`confint(::PowerDivergenceTest)`](@ref)

# References

  * Agresti, Alan. Categorical Data Analysis, 3rd Edition. Wiley, 2013.
