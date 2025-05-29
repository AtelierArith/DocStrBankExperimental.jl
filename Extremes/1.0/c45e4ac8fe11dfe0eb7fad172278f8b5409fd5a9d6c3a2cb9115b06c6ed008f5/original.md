```
gumbelfit(y,
    initialvalues,
    locationcov = Vector{Variable}(),
    logscalecov = Vector{Variable}()
    )
```

Estimate the Gumbel parameters.

# Arguments

  * `y::Vector{<:Real}`: the vector of block maxima.
  * `initialvalues::Vector{<:Real}`: Vector of parameters initial values.
  * `locationcov::Vector{<:DataItem} = Vector{Variable}()`: The covariates of the location parameter.
  * `logscalecov::Vector{<:DataItem} = Vector{Variable}()`: The covariates of the log-scale parameter.
