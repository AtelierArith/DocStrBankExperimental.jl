```julia
LinearRegression
```

Type representing the Linear Regression model class.

$$
y =\alpha +  X \beta+ \varepsilon,
$$

where 

$$
\varepsilon \sim N(0,\sigma^2),
$$

  * $y$ is the response vector of size $n$,
  * $X$ is the matrix of predictor variable of size $n \times p$,
  * $n$ is the sample size, and $p$ is the number of predictors,
  * $\alpha$ is the intercept of the model,
  * $\beta$ is the regression coefficients of the model, and
  * $\sigma$ is the standard deviation of the noise $\varepsilon$.
