```
BoxPierceTest(y, lag, dof=0)
```

Compute the Box-Pierce `Q` statistic to test the null hypothesis of independence in a time series `y`.

`lag` specifies the number of lags used in the construction of `Q`. When testing the residuals of an estimated model, `dof` has to be set to the number of estimated parameters. E.g., when testing the residuals of an ARIMA(p,0,q) model, set `dof=p+q`.

# External links

  * [Box-Pierce test on Wikipedia](https://en.wikipedia.org/wiki/Ljung–Box_test#Box-Pierce_test)
