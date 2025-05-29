```
Minuit structure
```

## Direct or calculated fields

  * `funcname::String` : Name of the function
  * `x0::AbstractVector` : Initial parameters values
  * `method::Symbol` : The minimization algorithm to use. Possible values are `:migrad`, `:simplex`
  * `tolerance::Real` : Tolerance for the minimization. If set to 0, Minuit will use a default value.
  * `precision::Union{Real,Nothing}` : The precision for the minimization
  * `strategy::Int` : The strategy for the minimization (0,1(default),2). See the manual for details.
  * `values` : The values of the parameters at the minimum
  * `errors` : The errors of the parameters at the minimum
  * `fixed` : The fixed status of the parameters
  * `limits` : The limits of the parameters
  * `is_valid` : If the minimization was successful
  * `fval` : The function value at the minimum
  * `edm` : The estimated distance to minimum
  * `nfcn` : The number of function calls
  * `ngrad` : The number of gradient calls
  * `niter` : The number of iterations
  * `npars` : The number of parameters
  * `ndof` : Number of degrees of freedom
  * `covariance` : The covariance matrix of the parameters
  * `is_above_max_edm` : If the estimated distance to minimum is above the maximum
  * `has_parameters_at_limit` : If any of the parameters are at the limits
  * `has_accurate_covar` : If the covariance matrix is accurate
  * `has_posdef_covar` : If the covariance matrix is positive definite
  * `has_made_posdef_covar` : If the covariance matrix was made positive definite
  * `hesse_failed` : If the Hesse algorithm failed
  * `has_covariance` : If the covariance matrix is available
  * `covariance` : The covariance matrix of the parameters
  * `has_accurate_covar` : If the covariance matrix is accurate
  * `has_valid_parameters` : If the parameters are valid
  * `has_reached_call_limit` : If the maximum number of function calls was reached
  * `minos` : The Minos errors
  * `parameters` : The parameters values and errors
