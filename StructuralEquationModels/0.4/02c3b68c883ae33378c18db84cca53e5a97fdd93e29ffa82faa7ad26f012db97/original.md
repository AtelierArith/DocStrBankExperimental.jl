For observed data with missing values.

# Constructor

```
SemObservedMissing(;
    data,
    observed_vars = nothing,
    specification = nothing,
    kwargs...)
```

# Arguments

  * `data`: observed data
  * `observed_vars::Vector{Symbol}`: column names of the data (if the object passed as data does not have column names, i.e. is not a data frame)
  * `specification`: optional SEM model specification ([`SemSpecification`](@ref))

# Extended help

## Interfaces

  * `nsamples(::SemObservedMissing)` -> number of samples (data points)
  * `nobserved_vars(::SemObservedMissing)` -> number of observed variables
  * `samples(::SemObservedMissing)` -> data matrix (contains both measured and missing values)

## Expectation maximization

`em_mvn!(::SemObservedMissing)` can be called to fit a covariance matrix and mean vector to the data using an expectation maximization (EM) algorithm under the assumption of multivariate normality. After, the following methods are available:

  * `em_model(::SemObservedMissing)` -> `EmMVNModel` that contains the covariance matrix and mean vector found via EM
  * `obs_cov(::SemObservedData)` -> EM covariance matrix
  * `obs_mean(::SemObservedData)` -> EM mean vector
