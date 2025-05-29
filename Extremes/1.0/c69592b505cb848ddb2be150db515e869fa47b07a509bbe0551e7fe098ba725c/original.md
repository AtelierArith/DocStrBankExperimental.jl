```
fit(pd::Type{<:GeneralizedPareto}, y::Vector{<:Real}; method::String="mle")
```

Fit the Generalized Pareto distribution to the exceedences vector `y`.

## Details

This function estimates the parameters of the GP distribution from an identically distributed random sample. It is a lightweight feature of the Extremes.jl library.

In the presence of non-stationarity or for advanced inference, the [`gpfit`](@ref) function is more appropriate.

The `method` argument allows selecting the estimation method: `mle` for maximum likelihood estimation or `pwm` for the probability-weighted moments method.
