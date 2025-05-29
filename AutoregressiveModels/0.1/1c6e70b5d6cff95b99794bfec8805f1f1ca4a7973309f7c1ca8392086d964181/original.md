```
fit(::Type{<:VARProcess}, data, names, nlag::Integer; kwargs...)
```

Estimate vector autoregression with ordinary least squares using `nlag` lags of variables indexed by `names` from a `Tables.jl`-compatible `data` table.

# Keywords

  * `subset::Union{BitVector, Nothing}=nothing`: subset of `data` to be used for estimation.
  * `choleskyresid::Bool=false`: conduct Cholesky factorization for the residual variance-covariance matrix.
  * `adjust_dofr::Bool=true`: adjust the degrees of freedom when computing the residual variance-covariance matrix.
  * `nocons::Bool=false`: do not include an intercept term in the estimation.
  * `TF::Type=Float64`: numeric type used for estimation.
