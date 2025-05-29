For observed data without missings.

# Constructor

```
SemObservedData(;
    data,
    observed_vars = nothing,
    specification = nothing,
    kwargs...)
```

# Arguments

  * `data`: observed data – *DataFrame* or *Matrix*
  * `observed_vars::Vector{Symbol}`: column names of the data (if the object passed as data does not have column names, i.e. is not a data frame)
  * `specification`: optional SEM specification ([`SemSpecification`](@ref))

# Extended help

## Interfaces

  * `nsamples(::SemObservedData)` -> number of observed data points
  * `nobserved_vars(::SemObservedData)` -> number of observed (manifested) variables
  * `samples(::SemObservedData)` -> observed data
  * `obs_cov(::SemObservedData)` -> observed covariance matrix
  * `obs_mean(::SemObservedData)` -> observed mean vector
