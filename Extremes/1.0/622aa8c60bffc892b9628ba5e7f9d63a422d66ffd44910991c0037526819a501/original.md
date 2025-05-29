```
gevfitbayes(y,
    locationcov = Vector{Variable}(),
    logscalecov = Vector{Variable}(),
    shapecov = Vector{Variable}(),
    niter::Int=5000,
    warmup::Int=2000
    )
```

Generate a sample from the GEV parameters' posterior distribution.

# Arguments

  * `y::Vector{<:Real}`: The vector of block maxima.
  * `locationcov::Vector{<:DataItem} = Vector{Variable}()`: The covariates of the location parameter.
  * `logscalecov::Vector{<:DataItem} = Vector{Variable}()`: The covariates of the log-scale parameter.
  * `shapecov::Vector{<:DataItem} = Vector{Variable}()`: The covariates of the shape parameter.
