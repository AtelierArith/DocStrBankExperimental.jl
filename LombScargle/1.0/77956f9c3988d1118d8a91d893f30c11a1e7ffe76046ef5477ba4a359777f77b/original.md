```
lombscargle(times::AbstractVector{<:Real}, signal::AbstractVector{<:Real},
            [errors::AbstractVector{<:Real}]; keywords...)
```

Compute the Lomb–Scargle periodogram of the `signal` vector, observed at `times`.  You can also specify the uncertainties for each signal point with `errors` argument.  All these vectors must have the same length.

All optional keywords are described in the docstring of [`LombScargle.plan`](@ref).

If the signal has uncertainties, the `signal` vector can also be a vector of `Measurement` objects (from [`Measurements.jl`](https://github.com/giordano/Measurements.jl) package), in which case you don’t need to pass a separate `errors` vector for the uncertainties of the signal.
