```
coef(lr::LinearRegressor)
```

Returns the linear regression coefficients of a [`linregress`](@ref) result. If `lr.intercept` is `true`, this includes the bias (intercept) in the last position.
