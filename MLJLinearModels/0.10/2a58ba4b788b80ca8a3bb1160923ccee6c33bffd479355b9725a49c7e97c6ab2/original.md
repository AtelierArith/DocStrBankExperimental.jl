```
GeneralizedLinearRegression{L<:Loss, P<:Penalty}
```

Generalized Linear Regression (GLR) model with objective function:

$L(y, Xθ) + P(θ)$

where `L` is a loss function, `P` a penalty, `y` is the vector of observed response, `X` is the feature matrix and `θ` the vector of parameters. If `scale_penalty_with_samples = true` (default) the penalty is automatically scaled with the number of samples.

Special cases include:

  * **OLS regression**:      L2 loss, no penalty.
  * **Ridge regression**:    L2 loss, L2 penalty.
  * **Lasso regression**:    L2 loss, L1 penalty.
  * **Logistic regression**: Logit loss, [no,L1,L2] penalty.
