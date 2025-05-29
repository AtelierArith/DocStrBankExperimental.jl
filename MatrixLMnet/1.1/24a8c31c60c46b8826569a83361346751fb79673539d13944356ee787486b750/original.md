```
admm!(X::AbstractArray{Float64,2}, Y::AbstractArray{Float64,2}, 
           Z::AbstractArray{Float64,2}, lambda::Float64, alpha::Float64,
           B::AbstractArray{Float64,2}, 
           regXidx::AbstractArray{Int64,1}, 
           regZidx::AbstractArray{Int64,1}, reg::BitArray{2}, norms, 
           Qx::AbstractArray{Float64,2}, Qz::AbstractArray{Float64,2}, 
           U::AbstractArray{Float64,2}, L::AbstractArray{Float64,2}; 
           isVerbose::Bool=true, stepsize::Float64=0.01, 
           rho::Float64=1.0, setRho::Bool=true, 
           thresh::Float64=10.0^(-7), maxiter::Int=10^10, 
           tau_incr::Float64=2.0, tau_decr::Float64=2.0, mu::Float64=10.0)
```

Performs ADMM. 

# Arguments

  * X = 2d array of floats consisting of the row covariates, with all  categorical variables coded in appropriate contrasts
  * Y = 2d array of floats consisting of the multivariate response
  * Z = 2d array of floats consisting of the column covariates, with all  categorical variables coded in appropriate contrasts
  * lambda = lambda penalty, a floating scalar
  * alpha = parameter (ϵ[0, 1]) determining the mix of penalties between L1 and L2
  * B = 2d array of floats consisting of starting coefficient estimates
  * regXidx = 1d array of indices corresponding to regularized X covariates
  * regZidx = 1d array of indices corresponding to regularized Z covariates
  * reg = 2d array of bits, indicating whether or not to regularize each of the  coefficients
  * norms = 2d array of floats consisting of the norms corresponding to each  coefficient or `nothing`
  * Qx = 2d array of floats consisting of the eigenvectors of X
  * Qz = 2d array of floats consisting of the eigenvectors of Z
  * U = 2d array of floats consisting of the transformed Y matrix
  * L = 2d array of floats consisting of the kronecker product of the  eigenvalues of X and Z

# Keyword arguments

  * isVerbose = boolean flag indicating whether or not to print messages.   Defaults to `true`.
  * stepsize = float; step size for updates (irrelevant for ADMM).  Defaults to `0.01`.
  * rho = float; parameter that controls ADMM tuning. Defaults to `1.0`.
  * setRho = boolean flag indicating whether the ADMM tuning parameter `rho`  should be calculated. Defaults to `true`.
  * thresh = threshold at which the coefficients are considered to have  converged, a floating scalar. Defaults to `10^(-7)`.
  * maxiter = maximum number of update iterations. Defaults to `10^10`.
  * tau_incr = float; parameter that controls the factor at which rho increases.  Defaults to 2.0.
  * tau_decr = float; parameter that controls the factor at which rho decreases.  Defaults to 2.0.
  * mu = float; parameter that controls the factor at which the primal and dual  residuals should be within each other. Defaults to 10.0.

# Value

None; updates coefficients in place

# Some notes

Convergence is determined as when the log ratio of the current and previous  criteria is less than the threshold `thresh`. 

`rho` controls ADMM tuning and can be specified by the user. 
