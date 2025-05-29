```
BreuschGodfreyTest(X, e, lag, start0 = true)
```

Compute the Breusch-Godfrey test for serial correlation in the residuals of a regression model.

`X` is the matrix of regressors from the original model and `e` the vector of residuals. `lag` determines the number of lagged residuals included in the auxiliary regression. Set `start0` to specify how the starting values for the lagged residuals are handled. `start0 = true` (default) sets them to zero (as in Godfrey, 1978); `start0 = false` uses the first `lag` residuals as starting values, i.e. shortening the sample by `lag`.

# External links

  * [Breusch-Godfrey test on Wikipedia](https://en.wikipedia.org/wiki/Breusch–Godfrey_test)
