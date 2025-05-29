```
SmoothLPResult{TF<:AbstractFloat, TS<:ModelSelectionResult} <: AbstractEstimatorResult
```

Additional results from estimating a smooth local projection. See also [`SmoothLP`](@ref) and [`LocalProjectionResult`](@ref).

# Fields

  * `θ::Vector{TF}`: coefficient estimates for the B-splines.
  * `Σ::Vector{TF}`: variance-covariance estimates for the B-splines.
  * `bm::Matrix{TF}`: basis matrix of the B-splines.
  * `λ::TF`: the optimal smoothing parameter from model selection.
  * `loocv::TF`: leave-one-out cross validation error.
  * `rss::TF`: residual sum of squares.
  * `gcv::TF`: generalized cross validation error.
  * `aic::TF`: Akaike information criterion value.
  * `dof_fit::TF`: degrees of freedom of the fit.
  * `dof_res::TF`: residual degrees of freedom.
  * `search::TS`: additional results from model selection.
  * `m::Ridge{TF}`: data from the ridge regression.
