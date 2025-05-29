```
arma_ssa(d::AbstractIdData, na, nc; L=nothing, estimator=\, robust=false)
```

Fit arma models using Singular Spectrum Analysis (SSA). A low-rank factorization (svd or robust svd) is performed on the data in order to decompose the signal and the noise. The noise is then used as input to fit an arma model.

See also [`arma`](@ref).

# Arguments:

  * `d`:  iddata
  * `na`: number of denominator parameters
  * `nc`: number of numerator parameters
  * `L`:  length of the lag-embedding used to separate signal and noise. `nothing` corresponds to automatic selection.
  * `estimator`: The function to solve the least squares problem. Examples `\,tls,irls,rtls`.
  * `robust`: Use robust PCA to be resistant to outliers.
