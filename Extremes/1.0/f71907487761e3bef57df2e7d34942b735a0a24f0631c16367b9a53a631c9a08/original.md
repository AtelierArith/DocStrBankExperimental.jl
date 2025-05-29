```
fit(pd::Type{<:GeneralizedExtremeValue}, y::Vector{<:Real}; method::String="mle")
```

Fit the Generalized Extreme Value distribution to the data vector `y`.

## Details

This function estimates the parameters of the GEV distribution from an identically distributed random sample. It is a lightweight feature of the Extremes.jl library.

In the presence of non-stationarity or for advanced inference, the [`gevfit`](@ref) function is more appropriate.

The `method` argument allows selecting the estimation method: `mle` for maximum likelihood estimation or `pwm` for the probability-weighted moments method.
