```julia
LogisticRegression
```

Type representing the Logistic Regression model class.

$$
y_i \sim Bernoulli(p_i), 
$$

where $i=1,2,\cdots,n, 0 < p_i < 1$, 

  * $\mathbb{E}(y_i)=p_i$,
  * $\mathbb{P}(y_i=1) = p_i$ and $\mathbb{P}(y_i=0) = 1-p_i$, such that

$$
\mathbb{E}(y_i)= p_i =g(\alpha +\mathbf{x}_i^T\beta),
$$

  * $g(.)$ is the link-function,
  * $y_i$ is the $i^{th}$ element of the response vector $y$,
  * $\mathbf{x}_i=(x_{i1},x_{i2},\cdots,x_{in})$ is the $i^{th}$ row of the design matix of size $n \times p$,
  * $\alpha$ is the intercept of the model, and
  * $\beta$ is the regression coefficients of the model.
