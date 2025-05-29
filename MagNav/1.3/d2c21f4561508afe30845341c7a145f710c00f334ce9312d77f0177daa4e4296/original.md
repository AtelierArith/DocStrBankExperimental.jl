```
linreg(y, x; λ=0)
```

Linear regression with data matrix.

**Arguments:**

  * `y`: length-`N` observed data vector
  * `x`: `N` x `Nf` input data matrix (`Nf` is number of features)
  * `λ`: (optional) ridge parameter

**Returns:**

  * `coef`: linear regression coefficients
