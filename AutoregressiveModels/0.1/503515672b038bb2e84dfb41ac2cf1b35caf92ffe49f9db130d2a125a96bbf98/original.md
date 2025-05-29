```
Factor{TF, S} <: RegressionModel
```

Results and cache from estimating a factor model. This object holds all arrays that are necessary for estimating the model without additional memory allocations. See also [`fit`](@ref) and [`fit!`](@ref).

# Fields

  * `Y::Matrix{TF}`: data matrix where each column corresponds to a time series.
  * `Ystd::Matrix{TF}`: standardized data with zero mean and unit standard deviation across the columns.
  * `Ysd::Vector{TF}`: standard deviation of each column in `Y`.
  * `Yca::Matrix{TF}`: cache of the same size as `Y`.
  * `fac::Matrix{TF}`: factors of the model; observed factors are placed in the beginning columns.
  * `crossfac::Matrix{TF}`: cache for holding `fac'fac` and factorization.
  * `Λ::Matrix{TF}`: loading matrix of the model; each row corresponds to a factor in `fac`.
  * `crossΛu::Union{Matrix{TF}, Nothing}`: cache needed when factors and loading matrix need to be solved iteratively.
  * `svdca::Union{SDDcache{TF}, SVDcache{TF}, Nothing}`: cache for singular value decomposition if any unobserved factor is involved.
  * `nfaco::Int`: number of observed factors.
  * `resid::Matrix{TF}`: residuals from the standardized data `Ystd` and estimated `fac` before scaling the loading matrix `Λ` for `Y`.
  * `tss::Vector{TF}`: total sum of squares for each columns of `Ystd`.
  * `rss::Vector{TF}`: residual sum of squares for each columns of `Ystd`.
  * `r2::Vector{TF}`: r-squared for each columns of `Ystd`.
  * `esample::BitVector`: indicators for rows involved in estimation from original data table when constructing `Y`; irrelevant to estimation once `Y` is given.
