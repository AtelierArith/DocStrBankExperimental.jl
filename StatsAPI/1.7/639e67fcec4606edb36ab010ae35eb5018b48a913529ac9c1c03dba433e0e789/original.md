```
adjr2(model::StatisticalModel)
adjr²(model::StatisticalModel)
```

Adjusted coefficient of determination (adjusted R-squared).

For linear models, the adjusted R² is defined as $1 - (1 - (1-R^2)(n-1)/(n-p))$, with $R^2$ the coefficient of determination, $n$ the number of observations, and $p$ the number of coefficients (including the intercept). This definition is generally known as the Wherry Formula I.
