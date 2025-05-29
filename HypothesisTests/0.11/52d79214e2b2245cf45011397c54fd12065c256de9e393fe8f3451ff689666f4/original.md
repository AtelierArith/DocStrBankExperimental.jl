```
WhiteTest(X, e; type = :White)
```

Compute White's (or Breusch-Pagan's) test for heteroskedasticity.

`X` is a matrix of regressors and `e` is the vector of residuals from the original model. The keyword argument `type` is either `:linear` for the Breusch-Pagan/Koenker test, `:linear_and_squares` for White's test with linear and squared terms only (no cross-products), or `:White` (the default) for the full White's test (linear, squared and cross-product terms). `X` should include a constant and at least one more regressor, with observations in rows and regressors in columns. In some applications, `X` is a subset of the regressors in the original model, or just the fitted values. This saves degrees of freedom and may give a more powerful test. The `lm` (Lagrange multiplier) test statistic is T*R2 where R2 is from the regression of `e^2` on the terms mentioned above. Under the null hypothesis it is distributed as `Chisq(dof)` where `dof` is the number of independent terms (not counting the constant), so the null is rejected when the test statistic is large enough.

Implements: [`pvalue`](@ref)

# References

  * H. White, (1980): A heteroskedasticity-consistent covariance matrix estimator and a direct test for heteroskedasticity, Econometrica, 48, 817-838.
  * T.S. Breusch & A.R. Pagan (1979), A simple test for heteroscedasticity and random coefficient variation, Econometrica, 47, 1287-1294
  * R. Koenker (1981), A note on studentizing a test for heteroscedasticity, Journal of Econometrics, 17, 107-112

# External links

  * [White's test on Wikipedia](https://en.wikipedia.org/wiki/White_test)
