```
linreg(y; λ=0)
```

Linear regression to determine best fit line for x = eachindex(y).

**Arguments:**

  * `y`: length-`N` observed data vector
  * `λ`: (optional) ridge parameter

**Returns:**

  * `coef`: length-`2` vector of linear regression coefficients
