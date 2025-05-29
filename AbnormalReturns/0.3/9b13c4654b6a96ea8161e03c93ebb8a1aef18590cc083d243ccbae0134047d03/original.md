```
alpha(rr::RegressionModel, coefname::String...="intercept")
```

"alpha" in respect to the the CAPM model, i.e., the intercept in the model. This is the alpha from the estimation period.

This function finds the position of the coefficient name provided, defaults to "intercept". If the coefname is not in the regression, then this function returns an error.
