```
DEModel{F,L,T,S} <: AbstractModel where {F <: Function,L,T,S}
```

A model object containing the log likelihood function and prior distributions.

# Fields

  * `prior_loglike::L`: log likelihood of posterior sample. A function must be defined for `sample`, but not for `optimize`.
  * `loglike::F`: a log likelihood function for Bayesian parameter estimation or an objective function for optimization.
  * `sample_prior::S`: a function for initial values. Typically, a prior distribution is ideal.
  * `names::T`: parameter names

# Constructor

```
function DEModel(
    args...; 
    prior_loglike = nothing, 
    loglike, 
    names, 
    sample_prior, 
    data, 
    kwargs...)
```

# Arguments

  * `args...`: optional positional arguments for `loglike`

# Keywords

  * `prior_loglike=nothing`: log likelihood of posterior sample. A function must be defined for `sample`, but not for `optimize`.
  * `loglike`: a log likelihood function for Bayesian parameter estimation or an objective function for optimization.
  * `sample_prior`: a function for initial values. Typically, a prior distribution is ideal.
  * `names`: parameter names
  * `kwargs...`: optional keyword arguments for `loglike`
