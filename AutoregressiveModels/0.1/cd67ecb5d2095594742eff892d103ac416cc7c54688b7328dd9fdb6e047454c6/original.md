```
simulate!(out::AbstractArray, εs::AbstractArray, arma::ARMAProcess, y0=nothing)
```

Simulate the `arma` process using the shocks specified in `εs` and initial values `y0`. Results are stored in `out`. If `y0` is `nothing` or does not contain enough lags, zeros are used. See also [`simulate`](@ref) and [`impulse!`](@ref).
