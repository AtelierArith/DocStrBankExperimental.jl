```
gpfitbayes(df::DataFrame,
    datacol::Symbol,
    logscalecovid = Vector{Symbol}(),
    shapecovid = Vector{Symbol}(),
    niter::Int=5000,
    warmup::Int=2000)
```

Generate a sample from the GP parameters' posterior distribution.

# Arguments

  * `df::DataFrame`: The dataframe containing the data.
  * `datacol::Symbol`: The symbol of the column of `df` containing the exceedances.
  * `logscalecovid::Vector{Symbol} = Vector{Symbol}()`: The symbols of the columns of `df` containing the covariates of the log-scale parameter.
  * `shapecovid::Vector{Symbol} = Vector{Symbol}()`: The symbols of the columns of `df` containing the covariates of the shape parameter.
