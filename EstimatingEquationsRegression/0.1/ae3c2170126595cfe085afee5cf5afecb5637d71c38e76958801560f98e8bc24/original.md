```
resid_pearson(m::AbstractGEE)
```

Return the Pearson residuals, which are the observed data minus the mean, divided by the square root of the variance function.  The scale parameter is not included so the Pearson residuals should have constant variance but not necessarily unit variance.
