```
gevfitbayes(df::DataFrame,
    datacol::Symbol,
    locationcovid = Vector{Symbol}(),
    logscalecovid = Vector{Symbol}(),
    shapecovid = Vector{Symbol}(),
    niter::Int=5000,
    warmup::Int=2000)
```

Generate a sample from the GEV parameters' posterior distribution.

# Arguments

  * `df::DataFrame`: The dataframe containing the data.
  * `datacol::Symbol`: The symbol of the column of `df` containing the block maxima data.
  * `locationcovid::Vector{Symbol} = Vector{Symbol}()`: The symbols of the columns of `df` containing the covariates of the location parameter.
  * `logscalecovid::Vector{Symbol} = Vector{Symbol}()`: The symbols of the columns of `df` containing the covariates of the log-scale parameter.
  * `shapecovid::Vector{Symbol} = Vector{Symbol}()`: The symbols of the columns of `df` containing the covariates of the shape parameter.
