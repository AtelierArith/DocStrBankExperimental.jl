```
gpfit(y,
    logscalecov = Vector{Variable}(),
    shapecov = Vector{Variable}()
    )
```

Estimate the GP parameters

# Arguments

  * `y::Vector{<:Real}`: The vector of exceedances.
  * `logscalecov::Vector{<:DataItem} = Vector{Variable}()`: The covariates of the log-scale parameter.
  * `shapecov::Vector{<:DataItem} = Vector{Variable}()`: The covariates of the shape parameter.
