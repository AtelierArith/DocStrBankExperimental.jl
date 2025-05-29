```
BrownForsytheTest(groups)
BrownForsytheTest(groups::AbstractVector{<:Real}...)
```

The Brown–Forsythe test is a statistical test for the equality of `groups` variances.

The Brown–Forsythe test is a modification of the Levene's test with the median instead of the mean statistic for computing the spread within each group.

Implements: [`pvalue`](@ref)

# References

  * Brown, Morton B.; Forsythe, Alan B., "Robust tests for the equality of variances". Journal of the American Statistical Association. 69: 364–367, 1974 doi:[10.1080/01621459.1974.10482955](https://doi.org/10.1080%2F01621459.1974.10482955).

# External links

  * [Brown–Forsythe test on Wikipedia ](https://en.wikipedia.org/wiki/Brown%E2%80%93Forsythe_test)
