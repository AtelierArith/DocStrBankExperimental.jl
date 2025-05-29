```
model = arma(d::AbstractIdData, na, nc; initial_order=20, method=:ls)
```

Estimate a Autoregressive Moving Average model with `na` coefficients in the denominator and `nc` coefficients in the numerator. Returns the model and the estimated noise sequence driving the system.

# Arguments:

  * `d`: iddata
  * `initial_order`: An initial AR model of this order is used to estimate the residuals
  * `estimator`: A function `(A,y)->minimizeₓ(Ax-y)` default is `\` but another option is `wtls_estimator(1:length(y)-initial_order,na,nc,ones(nc))`

See also [`estimate_residuals`](@ref)
