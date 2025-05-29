```
gpfitbayes(y,
    logscalecov = Vector{Variable}(),
    shapecov = Vector{Variable}(),
    niter::Int=5000,
    warmup::Int=2000
    )
```

Generate a sample from the GP parameters' posterior distribution.

# Arguments

  * `y::Vector{<:Real}`: The vector of exceedances.
  * `logscalecov::Vector{<:DataItem} = Vector{Variable}()`: The covariates of the log-scale parameter.
  * `shapecov::Vector{<:DataItem} = Vector{Variable}()`: The covariates of the shape parameter.
