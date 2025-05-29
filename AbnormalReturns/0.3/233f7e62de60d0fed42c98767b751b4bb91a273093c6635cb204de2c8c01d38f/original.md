```
beta(rr::RegressionModel, coefname::String...=["mkt", "mktrf", "vwretd", "ewretd"])
```

"beta" in respect to the CAPM model, i.e., the coefficient on the market return minus the risk free rate. This is the beta from the estimation period.

This function finds the position of the coefficient name provided, defaults to several common market returns. If the coefname is not in the regression, then this function returns an error.
