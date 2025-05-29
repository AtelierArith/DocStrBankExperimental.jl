inputs (required):      X: your design matrix, global intercept is assumed to be included (column of ones)

```
y: target class labels
```

inputs (optional):      lam: l2 (ridge) penalty. Larger values of lam will result in more regularization

```
verbose: bool deciding if the success or failure of optimization will be printed out
```

outputs:     tuple with estimated intercepts and coefficient matrix:       res = softmax_regression(X, y)      res.intercepts # to access the estimated intercepts      res.betas # to access the coefficient matrix
