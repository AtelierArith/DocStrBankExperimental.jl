```
DurbinWatsonTest(X::AbstractArray, e::AbstractVector; p_compute::Symbol = :ndep)
```

Compute the Durbin-Watson test for serial correlation in the residuals of a regression model.

`X` is the matrix of regressors from the original regression model and `e` the vector of residuals. Note that the Durbin-Watson test is not valid if `X` includes a lagged dependent variable. The test statistic is computed as

$$
DW = \frac{\sum_{t=2}^n (e_t - e_{t-1})^2}{\sum_{t=1}^n e_t^2}
$$

where `n` is the number of observations.

By default, the choice of approach to compute p-values depends on the sample size (`p_compute=:ndep`). For small samples (n<100), Pan's algorithm (Farebrother, 1980) is employed. For larger samples, a normal approximation is used (Durbin and Watson, 1950). To always use Pan's algorithm, set `p_compute=:exact`. `p_compute=:approx` will always use the normal approximation.

Default is a two-sided p-value for the alternative hypothesis of positive or negative serial correlation. One-sided p-values can be requested by calling `pvalue(x::DurbinWatsonTest; tail=)` with the options `:left` (negative serial correlation) and `:right` (positive serial correlation).

# References

  * J. Durbin and G. S. Watson, 1951, "Testing for Serial Correlation in Least Squares Regression: II", Biometrika, Vol. 38, No. 1/2, pp. 159-177, [http://www.jstor.org/stable/2332325](http://www.jstor.org/stable/2332325).
  * J. Durbin and G. S. Watson, 1950, "Testing for Serial Correlation in Least Squares Regression: I", Biometrika, Vol. 37, No. 3/4, pp. 409-428, [http://www.jstor.org/stable/2332391](http://www.jstor.org/stable/2332391).
  * R. W. Farebrother, 1980, "Algorithm AS 153: Pan's Procedure for the Tail Probabilities of the Durbin-Watson Statistic", Journal of the Royal Statistical Society, Series C (Applied Statistics), Vol. 29, No. 2, pp. 224-227, [http://www.jstor.org/stable/2986316](http://www.jstor.org/stable/2986316).

# External links

  * [Durbin-Watson test on Wikipedia](https://en.wikipedia.org/wiki/Durbin–Watson_statistic)
