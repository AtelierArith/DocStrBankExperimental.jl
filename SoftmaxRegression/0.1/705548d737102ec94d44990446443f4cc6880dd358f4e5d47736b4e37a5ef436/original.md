inputs (required):      params: vector (contains n*intercepts + length(vec(betas)) parameters)             this is a concatenated 1-d vector of all parameters you wish the estimate             the intercept terms should be first, and you should have n*class - 1 of them.              After comes the vectorized coefficient matrix

```
X: your design matrix, global intercept is assumed to be included (column of ones)

y: target class labels
```

outputs:      negative log-likelihood which is optionally penalized
