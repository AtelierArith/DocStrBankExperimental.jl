```
BreuschPaganTest(X, e)
```

Compute Breusch-Pagan's test for heteroskedasticity.

`X` is a matrix of regressors from the original model and `e` the vector of residuals. This is equivalent to `WhiteTest(X, e, type = :linear)`. See [`WhiteTest`](@ref) for further details.
