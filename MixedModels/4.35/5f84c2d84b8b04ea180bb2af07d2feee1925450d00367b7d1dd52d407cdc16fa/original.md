```
stderror!(v::AbstractVector, m::LinearMixedModel)
```

Overwrite `v` with the standard errors of the fixed-effects coefficients in `m`

The length of `v` should be the total number of coefficients (i.e. `length(coef(m))`). When the model matrix is rank-deficient the coefficients forced to `-0.0` have an undefined (i.e. `NaN`) standard error.
