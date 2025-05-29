```
impulse!(out, r::VectorAutoregression, ε0::AbstractVecOrMat; kwargs...)
impulse!(out, r::VectorAutoregression, ishock::Union{Integer, AbstractRange}; kwargs...)
```

Compute impulse responses to shocks specified with `ε0` or `ishock` based on the estimation result in `r` and store the results in an array `out`. The number of horizons to be computed is determined by the second dimension of `out`. Responses to structural shocks identified based on temporal (short-run) restrictions can be computed if Cholesky factorization has been conducted for `r`. See also [`impulse`](@ref) and [`simulate!`](@ref).

As a vector, `ε0` specifies the magnitude of the impulse to each variable; columns in a matrix are interpreted as multiple impulses with results stored separately along the third dimension of array `out`. Alternatively, `ishock` specifies the index of a single variable that is affected on impact; a range of indices is intercepted as multiple impulses. With the keyword `choleskyshock` being `true`, any shock index specified is interpreted as referring to the structural shock instead of the reduced-form shock.

# Keywords

  * `nlag::Integer=arorder(var)`: the number of lags from `var` used for simulations.
  * `choleskyshock::Bool=false`: whether any shock index refers to a structural shock.
