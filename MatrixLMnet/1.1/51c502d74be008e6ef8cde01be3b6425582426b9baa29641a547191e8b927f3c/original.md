```
fista_bt!(X::AbstractArray{Float64,2}, Y::AbstractArray{Float64,2}, 
               Z::AbstractArray{Float64,2}, lambda::Float64, alpha::Float64,
               B::AbstractArray{Float64,2}, 
               regXidx::AbstractArray{Int64,1}, 
               regZidx::AbstractArray{Int64,1}, reg::BitArray{2}, norms; 
               isVerbose::Bool=true, stepsize::Float64=0.01, 
               gamma::Float64=0.5, thresh::Float64=10.0^(-7), 
               maxiter::Int=10^10)
```

Performs FISTA with backtracking. 

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

# Keyword arguments

  * isVerbose = boolean flag indicating whether or not to print messages.   Defaults to `true`.
  * stepsize = float; step size for updates. Defaults to `0.01`.
  * gamma = float; multiplying factor for step size backtracking/line search.  Defaults to `0.5`.
  * thresh = threshold at which the coefficients are considered to have  converged, a floating scalar. Defaults to `10^(-7)`.
  * maxiter = maximum number of update iterations. Defaults to `10^10`.

# Value

None; updates coefficients in place

# Some notes

Convergence is determined as when the log ratio of the current and previous  criteria is less than the threshold `thresh`. 

Specifying a good starting step size (`stepsize`) and multiplying factor  (`gamma`) in the `mlmnet` function when `fista_bt!` is passed into the `fun`  argument can be difficult. Shrinking the step size too gradually can result  in slow convergence. Doing so too quickly can cause the criterion to diverge.  We have found that setting `stepsize` to 0.01 often works well in practice;  choice of `gamma` appears to be less consequential. 
