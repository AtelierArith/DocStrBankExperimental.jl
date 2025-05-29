```julia
NegBinomRegression
```

Type representing the Negative Binomial Regression model class.

$$
y_i \sim NegativeBinomial(\mu_i,\phi), i=1,2,\cdots,n
$$

where

$$
\mu_i = \exp(\alpha +\mathbf{x}_i^T\beta),
$$

  * $y_i$ is the $i^{th}$ element of the response vector $y$,
  * $\mathbf{x}=(x_{i1},x_{i2},\cdots,x_{in})$ is the $i^{th}$ row of the design matix of size $n \times p$,
  * $\alpha$ is the intercept of the model, and
  * $\beta$ is the regression coefficients of the model.
