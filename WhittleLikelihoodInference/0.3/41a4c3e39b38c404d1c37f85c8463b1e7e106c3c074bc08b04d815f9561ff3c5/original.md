```
fit(ts,Δ;model::Type{<:TimeSeriesModel},x₀,lowerΩcutoff,upperΩcutoff,x_lowerbounds,x_upperbounds,method,taper)
fit(timeseries::TimeSeries;model::Type{<:TimeSeriesModel},x₀,lowerΩcutoff,upperΩcutoff,x_lowerbounds,x_upperbounds,method,taper)
```

Fit a time series model using the `IPNewton` method from Optim.jl.

# Arguments

  * `ts`: `n` by `D` matrix containing the timeseries (or vector if `D=1`), where `n` is the number of observations and `D` is the number of series.
  * `Δ`: The sampling rate, which should be a positive real number.
  * `timeseries`: Can be provided in place of `ts` and `Δ`.
  * `model`: The model which will be fitted. Should be a type (not a realisation of the model) e.g. JONSWAP{k} not JONSWAP{K}(x).
  * `x₀`: The initial parameter guess.
  * `lowerΩcutoff`: The lower cutoff for the frequency range to be used in fitting. Default is `0`.
  * `upperΩcutoff`: The upper cutoff for the frequency range to be used in fitting. Default is `Inf`.
  * `x_lowerbounds`: The lower bounds on the parameter space. If `nothing` is provided (the default) then these are set to default values based on the model.
  * `x_upperbounds`: The upper bounds on the parameter space. If `nothing` is provided (the default) then these are set to default values based on the model.
  * `method`: Either `:Whittle` or `:debiasedWhittle`.
  * `taper`: The choice of tapering to be used. This should be `nothing` (in which case no taper is used) or `dpss_nw` where `nw` time-bandwith product (see DSP.dpss for more details).
  * `options`: Options for optimisation of type `Optim.Options`.
