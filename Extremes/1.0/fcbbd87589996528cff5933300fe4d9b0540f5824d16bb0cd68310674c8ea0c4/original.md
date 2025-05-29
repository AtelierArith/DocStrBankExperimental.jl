```
gevfit(y,
    initialvalues,
    locationcov = Vector{Variable}(),
    logscalecov = Vector{Variable}(),
    shapecov = Vector{Variable}()
    )
```

Estimate the GEV parameters.

# Arguments

  * `y::Vector{<:Real}`: the vector of block maxima.
  * `initialvalues::Vector{<:Real}`: Vector of parameters initial values.
  * `locationcov::Vector{<:DataItem} = Vector{Variable}()`: The covariates of the location parameter.
  * `logscalecov::Vector{<:DataItem} = Vector{Variable}()`: The covariates of the log-scale parameter.
  * `shapecov::Vector{<:DataItem} = Vector{Variable}()`: The covariates of the shape parameter.
