```
linregress(X, y; intercept=true, method=SolveQR())
linregress(X, y, weights; intercept=true, method=SolveQR())
```

Do (possibly weighted) linear regression to obtain coefficients β such that `ŷ = X * β` minimizes `‖ŷ - y‖²`. In the default case, this corresponds to solving `X \ y`.

Returns a `LinearRegressor`, which can be passed to [`coef`](@ref) to extract the coefficients β or called with a vector or matrix `X` to predict at a single point or set of points.

Currently assumes that, if `X` is a Matrix, that `size(X) == (length(y), num_coefs)` (i.e., each row describes the features for one observation).

## Keyword Arguments:

  * If `intercept` is `true`, implicitly adds a column of ones to `X` to model a bias term.
  * `method` determines how to solve the linear regression system (see [`SolveQR`](@ref) and [`SolveCholesky`](@ref)).
