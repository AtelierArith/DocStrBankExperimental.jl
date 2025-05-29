```
gpfit(df::DataFrame,
    datacol::Symbol,
    logscalecovid = Vector{Symbol}(),
    shapecovid = Vector{Symbol}()
    )
```

Estimate the GP parameters

# Arguments

  * `df::DataFrame`: The dataframe containing the data.
  * `datacol::Symbol`: The symbol of the column of `df` containing the exceedances.
  * `initialvalues::Vector{<:Real}`: Vector of parameters initial values.
  * `logscalecovid::Vector{Symbol} = Vector{Symbol}()`: The symbols of the columns of `df` containing the covariates of the log-scale parameter.
  * `shapecovid::Vector{Symbol} = Vector{Symbol}()`: The symbols of the columns of `df` containing the covariates of the shape parameter.
