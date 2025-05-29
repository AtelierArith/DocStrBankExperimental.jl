```
fit_linear_data(x_data, y_data)
```

Fit two vectors of data to a linear model and return their slope and intercept.  Both the slope and intercept will be `measurement` types, with the uncertainty being the standard error of the fittings. 

!!! note
    If the input data are `measurement`s, the `y_data` uncertainties will be used to weight the importance of each data point. [Alexander Aitken](https://en.wikipedia.org/wiki/Alexander_Aitken) showed that weighting according to the inverse of variance is the [best linear unbiased estimator (BLUE)](https://en.wikipedia.org/wiki/Gauss%E2%80%93Markov_theorem). Read more on weighted least squares in linear regression [here](https://en.wikipedia.org/wiki/Weighted_least_squares).

