```
simulate!(εs::AbstractArray, r::VectorAutoregression, Y0=nothing; kwargs...)
```

Simulate the [`VARProcess`](@ref) with the coefficient estimates in `r` using the shocks specified in `εs` and initial values `Y0`. Results are stored by overwriting `εs` in-place. If `Y0` is `nothing` or does not contain enough lags, zeros are used. See also [`simulate`](@ref) and [`impulse!`](@ref).

# Keywords

  * `nlag::Integer=arorder(var)`: the number of lags from `var` used for simulations.
