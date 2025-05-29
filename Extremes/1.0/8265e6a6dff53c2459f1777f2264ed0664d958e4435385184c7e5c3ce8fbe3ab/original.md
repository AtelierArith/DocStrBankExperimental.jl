```
gumbelfit(y,
    locationcov = Vector{Variable}(),
    logscalecov = Vector{Variable}()
    )
```

Estimate the Gumbel parameters.

# Arguments

  * `y::Vector{<:Real}`: The vector of block maxima.
  * `locationcov::Vector{<:DataItem} = Vector{Variable}()`: The covariates of the location parameter.
  * `logscalecov::Vector{<:DataItem} = Vector{Variable}()`: The covariates of the log-scale parameter.
