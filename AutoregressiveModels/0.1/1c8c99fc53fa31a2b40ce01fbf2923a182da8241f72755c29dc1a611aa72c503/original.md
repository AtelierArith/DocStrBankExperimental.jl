```
impulse!(out, var::VARProcess, ε0::AbstractVecOrMat; kwargs...)
impulse!(out, var::VARProcess, ishock::Union{Integer, AbstractRange}; kwargs...)
```

Compute the responses of the `var` process to the impulse specified with `ε0` or `ishock` and store the results in an array `out`. The number of horizons to be computed is determined by the second dimension of `out`. See also [`impulse`](@ref) and [`simulate!`](@ref).

As a vector, `ε0` specifies the magnitude of the impulse to each variable; columns in a matrix are interpreted as multiple impulses with results stored separately along the third dimension of array `out`. Alternatively, `ishock` specifies the index of a single variable that is affected on impact; a range of indices is intercepted as multiple impulses.

# Keywords

  * `nlag::Integer=arorder(var)`: the number of lags from `var` used for simulations.
