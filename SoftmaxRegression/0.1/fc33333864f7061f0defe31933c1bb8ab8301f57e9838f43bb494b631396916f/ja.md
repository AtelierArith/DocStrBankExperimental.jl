inputs (required):      params: vector (contains n*intercepts + length(vec(betas)) parameters)             this is a concatenated 1-d vector of all parameters you wish the estimate             the intercept terms should be first, and you should have n*class of them.              After comes the vectorized coefficient matrix

```
X: your design matrix, global intercept is assumed to be included (column of ones)

y: target class labels

lam: l2 (ridge) penalty. Larger values of lam will result in more regularization
```

outputs:      negative log-likelihood which is optionally penalized
