```
hdmm(X::Matrix{<:Real}, G::Matrix{<:Real}, y::Vector{<:Real}, 
     grp::Vector{<:Union{String, Int64}}, Z::Matrix{<:Real}=X; 
     <keyword arguments>)
```

Fit a penalized linear mixed effect model using the coordinate gradient descent (CGD)  algorithm and return a fitted model of type `HDMModel`. 

# Arguments

  * `X`: Low dimensional (N by q) design matrix for unpenalized fixed effects (**first column must be all 1's to fit intercept**)
  * `G`: High dimensional (N by p) design matrix for penalized fixed effects (**should not include column of 1's**)
  * `y`: Length N response vector
  * `grp`: Length N vector with group assignments of each observation
  * `Z=X`: Random effects design matrix (N by m), should contain some subset of the columns of `X` (defaults to equal `X`)

Keyword: 

  * `penalty::String="scad"`: Either "scad" or "lasso"
  * `standardize::Bool=true`: Whether to standardize the columns of all design matrices before performing coordinate descent. The value of `λ` (and `wts`) should be chosen accordingly. Estimates will be returned to the original scale at the end.
  * `λ::Real=10.0`: Positive number providing the regularization parameter for the penalty
  * `wts::Union{Vector,Nothing}=nothing`: If specified, the penalty on covariate j will be λ/wⱼ, so this argument is useful if you want to penalize some covariates more than others.
  * `scada::Real=3.7`: Positive number providing the extra tuning parameter for the scad penalty (ignored for lasso)
  * `max_active`::Real=length(y)/2: Maximum number of fixed effects estimated non-zero (defaults to half the total sample size)
  * `ψstr::String="diag"`: One of "ident", "diag", or "sym", specifying the structure of the random effects' covariance matrix
  * `init_coef::Union{Tuple,Nothing} = nothing`: If specified, provides the initialization to the algorithm. See notes below for more details
  * `control::Control = Control()`: Custom struct with hyperparameters of the CGD algorithm, defaults are in documentation of `Control` struct

# Notes

The initialization to the descent algorithm can be specified in the `init_coef` argument as a tuple of the form (β, L, σ²), where

  * β is a vector of length p + q providing an initial estimate of the fixed effect coefficients
  * L is the Cholesky factor of the random effect covariance matrix, and is represented as 

      * a scalar if ψstr="ident"
      * a vector of length m if ψstr="diag"
      * a lower triangular matrix of size m by m if ψstr="sym"
  * σ² is a scalar providing an initial estimate of the noise variance

If the `init_coef` argument is not specified, we obtain initial parameter estimates in the following manner:

1. A LASSO that ignores random effects (with λ chosen using cross validation) is performed to estimate the fixed effect parameters.
2. L, assumed temporarilly to be a scalar, and σ² are estimated to maximize the likelihood given these estimated fixed effect parameters.
3. If `ψstr` is "diag" or "sym", the scalar L is converted to a vector or matrix by repeating the scalar or filling the diagonal of a matrix with the scalar, respectively.
