```
SemObservedCovariance(;
    specification,
    obs_cov,
    nsamples,
    obs_mean = nothing,
    observed_vars = nothing,
    kwargs...)
```

Construct [`SemObserved`](@ref) without providing the observations data, but with the covariations (`obs_cov`) and the means (`obs_means`) of the observed variables.

Returns [`SemObservedCovariance`](@ref) object.

# Arguments

  * `obs_cov`: pre-computed covariance matrix of the observed variables
  * `nsamples::Integer`: number of samples (observed data points) used to compute `obs_cov` and `obs_means`,  used for calculating fit statistics
  * `obs_mean`: optional pre-computed means of the observed variables
  * `observed_vars::AbstractVector`: IDs of the observed variables (rows and columns of the `obs_cov` matrix)
  * `specification`: optional SEM specification ([`SemSpecification`](@ref))
