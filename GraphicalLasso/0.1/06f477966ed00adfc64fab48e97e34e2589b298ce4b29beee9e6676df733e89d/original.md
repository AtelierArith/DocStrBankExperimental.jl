```
glasso(s::Matrix{Float64}, obs::Int, λ::Real; penalizediag::Bool=true, γ::Real=0.0, tol::Float64=1e-05, verbose::Bool=true, maxiter::Int=100, winit::Matrix{Float64}=zeros(size(s)))
```

Applies the graphical lasso (glasso) algorithm to estimate a sparse inverse covariance matrix.

# Arguments

  * `s::Matrix{Float64}`: Empirical covariance matrix.
  * `obs::Int`: Number of observations.
  * `λ::Real`: Regularization parameter for the lasso penalty.
  * `penalizediag::Bool=true`: Whether to penalize the diagonal entries. (optional)
  * `γ::Real=0.0`: EBIC tuning parameter. (optional)
  * `tol::Float64=1e-05`: Tolerance for the convergence criteria. (optional)
  * `verbose::Bool=true`: If true, prints convergence information. (optional)
  * `maxiter::Int=100`: Maximum number of iterations. (optional)
  * `winit::Matrix{Float64}=zeros(size(s))`: Initial value of the precision matrix. (optional)

# Returns

  * `NamedTuple`: A named tuple with fields:

      * `W::Matrix{Float64}`: Estimated precision matrix.
      * `θ::Matrix{Float64}`: Estimated inverse covariance matrix.
      * `ll::Float64`: Log-likelihood of the estimate.
      * `bicval::Float64`: EBIC value of the estimate.
