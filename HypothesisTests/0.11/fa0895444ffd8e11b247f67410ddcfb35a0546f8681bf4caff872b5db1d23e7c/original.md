```
MultinomialLRTest(x[, y][, theta0 = ones(length(x))/length(x)])
```

Perform a multinomial likelihood ratio test (equivalent to a [`PowerDivergenceTest`](@ref) with $λ = 0$).

If `y` is not given and `x` is a matrix with one row or column, or `x` is a vector, then a goodness-of-fit test is performed (`x` is treated as a one-dimensional contingency table). In this case, the hypothesis tested is whether the population probabilities equal those in `theta0`, or are all equal if `theta0` is not given.

If `x` is a matrix with at least two rows and columns, it is taken as a two-dimensional contingency table. Otherwise, `x` and `y` must be vectors of the same length. The contingency table is calculated using `counts` function from the `StatsBase` package. Then the power divergence test is conducted under the null hypothesis that the joint distribution of the cell counts in a 2-dimensional contingency table is the product of the row and column marginals.

Note that the entries of `x` (and `y` if provided) must be non-negative integers.

Implements: [`pvalue`](@ref), [`confint`](@ref)
