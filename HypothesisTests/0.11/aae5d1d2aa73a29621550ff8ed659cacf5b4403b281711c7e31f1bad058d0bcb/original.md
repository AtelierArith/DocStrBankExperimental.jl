```
ShapiroWilkTest(X::AbstractVector{<:Real},
                swc::AbstractVector{<:Real}=shapiro_wilk_coefs(length(X));
                sorted::Bool=issorted(X),
                censored::Integer=0)
```

Perform a Shapiro-Wilk test of the null hypothesis that the data in vector `X` come from a normal distribution.

This implementation is based on the method by Royston (1992). The calculation of the p-value is exact for sample size `N = 3`, and for ranges `4 ≤ N ≤ 11` and `12 ≤ N ≤ 5000` (Royston 1992) two separate approximations for p-values are used.

# Keyword arguments

The following keyword arguments may be passed.

  * `sorted::Bool=issorted(X)`: to indicate that sample `X` is already sorted.
  * `censored::Integer=0`: to censor the largest samples from `X` (so called upper-tail censoring)

Implements: [`pvalue`](@ref)

!!! warning
    As noted by Royston (1993), (approximated) W-statistic will be accurate but returned p-values may not be reliable if either of these apply:

      * Sample size is large  (`N > 2000`) or small (`N < 20`)
      * Too much data is censored (`censored / N > 0.8`)


# Implementation notes

  * The current implementation DOES NOT implement p-values for censored data.
  * If multiple Shapiro-Wilk tests are to be performed on samples of same size, it is faster to construct `swc = shapiro_wilk_coefs(length(X))` once and pass it to the test via `ShapiroWilkTest(X, swc)` for re-use.
  * For maximal performance sorted `X` should be passed and indicated with `sorted=true` keyword argument.

# References

Shapiro, S. S., & Wilk, M. B. (1965). An Analysis of Variance Test for Normality (Complete Samples). *Biometrika*, 52, 591–611. [doi:10.1093/BIOMET/52.3-4.591](https://doi.org/10.1093/BIOMET/52.3-4.591).

Royston, P. (1992). Approximating the Shapiro-Wilk W-test for non-normality. *Statistics and Computing*, 2(3), 117–119. [doi:10.1007/BF01891203](https://doi.org/10.1007/BF01891203)

Royston, P. (1993). A Toolkit for Testing for Non-Normality in Complete and Censored Samples. Journal of the Royal Statistical Society Series D (The Statistician), 42(1), 37–43. [doi:10.2307/2348109](https://doi.org/10.2307/2348109)

Royston, P. (1995). Remark AS R94: A Remark on Algorithm AS 181: The W-test for Normality. *Journal of the Royal Statistical Society Series C (Applied Statistics)*, 44(4), 547–551. [doi:10.2307/2986146](https://doi.org/10.2307/2986146).
