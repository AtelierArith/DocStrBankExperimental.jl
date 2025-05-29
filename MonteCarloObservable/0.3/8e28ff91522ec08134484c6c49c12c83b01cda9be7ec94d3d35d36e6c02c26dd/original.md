```
export_results(obs::Observable{T}[, filename::AbstractString, group::AbstractString; timeseries::Bool=false])
```

Export result for given observable nicely to JLD.

Will export name, number of measurements, estimates for mean and one-sigma error. Optionally (`timeseries==true`) exports the full time series as well.
